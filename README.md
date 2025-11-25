# 一键部署 Xray 节点（VMESS + SOCKS5）

本项目提供 **VMESS** 和 **SOCKS5** 两种 Xray 节点的一键部署脚本，方便快速搭建可用代理节点，适用于 Nodejs/Python 或 Pterodactyl 翼龙面板。

# 1. VMESS 在 Nodejs/Python 一键脚本极简部署（Pterodactyl 翼龙面板）
* 自动生成服务端配置，无需手动设置端口
* 客户端链接自动生成，支持导入 V2Ray、小火箭等客户端使用
* 启动 VMESS 节点并生成可用客户端链接

```bash
curl -Ls https://raw.githubusercontent.com/wuya110/wispbyte/refs/heads/main/vess | sed 's/\r$//' | bash
```

生成文件：
- 服务端配置：`vmess.json`
- 客户端链接：`vmess_link.txt`

# 2. SOCKS5 在 Nodejs/Python 一键脚本极简部署（Pterodactyl 翼龙面板）
* 自动下载并启动 Xray SOCKS5 节点
* 自动绑定公网 IP，保证外网可访问
* 客户端链接自动生成，格式为 `socks5://user:pass@公网IP:端口`
* 可直接导入小火箭或 CF Worker 使用

```bash
curl -Ls https://raw.githubusercontent.com/wuya110/wispbyte/refs/heads/main/socks5 | sed 's/\r$//' | bash
```

生成文件：
- 配置文件：`socks5.json`
- 客户端链接：输出 `socks5://user:pass@公网IP:端口`

# ⚠️ 注意事项
* VPS 防火墙或安全组必须放行对应端口（TCP/UDP）
* SOCKS5 链接必须是 `socks5://user:pass@IP:PORT` 才兼容多数客户端
* 确保 VPS 公网 IP 可访问，否则客户端无法连接

# 📌 使用示例
### 小火箭导入
- 类型：VMESS 或 SOCKS5
- 链接/IP：脚本生成的客户端链接
- 端口：对应端口
- 用户名/密码：SOCKS5 使用 `user` / `pass`

### CF Worker 使用
- 直接使用 `socks5://user:pass@公网IP:端口` 作为代理
