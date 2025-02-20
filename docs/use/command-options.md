| 名称 | 含义 | 选项值 |
| :-: | :-: | :-: |
| `--source` | 指定软件源地址 | 地址 |
| `--source-security` | 指定 debian 的 security 软件源地址 | 地址 |
| `--source-vault` | 指定 centos/almalinux 的 vault 软件源地址 | 地址 |
| `--branch` | 指定软件源分支(路径) | 分支名 |
| `--branch-security` | 指定 debian 的 security 软件源分支(路径) | 分支名 |
| `--branch-vault` | 指定 centos/almalinux 的 vault 软件源分支(路径) | 分支名 |
| `--abroad` | 使用海外软件源 | 无 |
| `--abroad` | 使用中国大陆教育网软件源 | 无 |
| `--web-protocol` | 指定 WEB 协议 | `http` 或 `https` |
| `--intranet` | 优先使用内网地址 | `true` 或 `false` |
| `--install-epel` | 安装 EPEL 附加软件包 | `true` 或 `false` |
| `--only-epel` | 仅更换 EPEL 软件源模式 | 无 |
| `--close-firewall` | 关闭防火墙 | `true` 或 `false` |
| `--backup` | 备份原有软件源 | `true` 或 `false` |
| `--ignore-backup-tips` | 忽略覆盖备份提示（即不覆盖备份） | 无 |
| `--updata-software` | 更新软件包 | `true` 或 `false` |
| `--clean-cache` | 清理下载缓存 | `true` 或 `false` |
| `--print-diff` | 打印源文件修改前后差异 | `true` 或 `false` |
| `--help` | 查看帮助菜单 | 无 |

## 示例

### 指定软件源地址

若不想通过交互选择默认提供的软件源，你可以使用该命令选项指定软件源地址

``` { .bash .no-copy }
bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
    --source mirror.example.com
```

### 指定软件源分支

使用场景：目标软件源有对应系统镜像但是不符合本脚本关于软件源分支设置的默认规则  

本脚本为了适配大的环境不会针对某一镜像站独特的镜像分支名称而单独定制，最开始是为了更换国内软件源而设计适配的，默认使用的分支名称如下

<table>
<tr>
    <td><a href="https://www.debian.org" target="_blank"><img src="/../assets/images/icon/debian.svg" width="16" height="16" style="vertical-align: -0.45em"/></a>&nbsp;Debian</td>
    <td align="center">debian</td>
</tr>
<tr>
    <td><a href="https://cn.ubuntu.com" target="_blank"><img src="/../assets/images/icon/ubuntu.svg" width="16" height="16" style="vertical-align: -0.15em"/></a>&nbsp;Ubuntu</td>
    <td align="center">ubuntu/ubuntu-ports</td>
</tr>
<tr>
    <td><a href="https://www.kali.org" target="_blank"><img src="/../assets/images/icon/kali-linux.svg" width="16" height="16"/></a>&nbsp;Kali Linux</td>
    <td align="center">kali</td>
</tr>
<tr>
    <td><a href="https://access.redhat.com/products/red-hat-enterprise-linux" target="_blank"><img src="/../assets/images/icon/redhat.svg" width="16" height="16" style="vertical-align: -0.15em"/></a>&nbsp;Red Hat Enterprise Linux</td>
    <td align="center">centos/rocky</td>
</tr>
<tr>
    <td><a href="https://fedoraproject.org/zh-Hans" target="_blank"><img src="/../assets/images/icon/fedora.ico" width="16" height="16" style="vertical-align: -0.15em"/></a>&nbsp;Fedora</td>
    <td align="center">fedora</td>
</tr>
<tr>
    <td><a href="https://www.centos.org" target="_blank"><img src="/../assets/images/icon/centos.svg" width="16" height="16" style="vertical-align: -0.15em"/></a>&nbsp;CentOS</td>
    <td align="center">centos/centos-stream/centos-altarch/centos-vault</td>
</tr>
<tr>
    <td><a href="https://rockylinux.org" target="_blank"><img src="/../assets/images/icon/rocky-linux.svg" width="16" height="16" style="vertical-align: -0.25em"/></a>&nbsp;Rocky Linux</td>
    <td align="center">rocky</td>
</tr>
<tr>
    <td><a href="https://almalinux.org/zh-hans" target="_blank"><img src="/assets/images/icon/almalinux.svg" width="16" height="16" style="vertical-align: -0.25em"/></a>&nbsp;AlmaLinux</td>
    <td align="center">almalinux/almalinux-vault</td>
</tr>
<tr>
    <td><a href="https://www.opencloudos.org" target="_blank"><img src="/assets/images/icon/opencloudos.png" width="16" height="16" style="vertical-align: -0.25em"/></a>&nbsp;OpenCloudOS</td>
    <td align="center">opencloudos</td>
</tr>
<tr>
    <td><a href="https://www.openeuler.org/zh" target="_blank"><img src="/../assets/images/icon/openeuler.ico" width="16" height="16" style="vertical-align: -0.25em"/></a>&nbsp;openEuler</td>
    <td align="center">openeuler</td>
</tr>
<tr>
    <td><a href="https://www.opensuse.org" target="_blank"><img src="/../assets/images/icon/opensuse.svg" width="16" height="16" style="vertical-align: -0.25em"/></a>&nbsp;openSUSE</td>
    <td align="center">opensuse</td>
</tr>
<tr>
    <td><a href="https://archlinux.org" target="_blank"><img src="/../assets/images/icon/arch-linux.ico" width="16" height="16" style="vertical-align: -0.15em"/></a>&nbsp;Arch Linux</td>
    <td align="center">archlinux/archlinuxarm</td>
</tr>
</table>

请看下面的例子

``` { .bash .no-copy title="使用阿里云的 Rocky Linux 软件源" }
bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
  --source mirrors.aliyun.com \
  --branch rockylinux
```

阿里云镜像站的 Rocky Linux 镜像分支名称为 [`rockylinux`](https://mirrors.aliyun.com/rockylinux)，不符合默认规则，但是可以通过命令选项绕过脚本默认规则来实现

### 单独更换 EPEL 源

有些时候你会发现想使用的镜像站没有 epel 镜像仓库，那么你可以在第一次运行脚本时不安装或不更换 epel 源，然后再单独执行下面的命令

``` bash
bash <(curl -sSL https://linuxmirrors.cn/main.sh) --only-epel
```

### 自定义 Debian Security 源

如果你想尽可能提高服务器的安全性则建议使用官方源，因为镜像同步存在延迟

``` bash
bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
  --source-security security.debian.org \
  --branch-security debian-security
```

## 无人值守

不通过交互完成换源操作，需要使用大量命令选项来实现，建议熟悉后再使用

``` { .bash .no-copy title="参考命令" }
bash <(curl -sSL https://linuxmirrors.cn/main.sh) \
  --source mirror.example.com \
  --web-protocol http \
  --intranet false \
  --install-epel true \
  --close-firewall true \
  --backup true \
  --updata-software false \
  --clean-cache false \
  --ignore-backup-tips
```
