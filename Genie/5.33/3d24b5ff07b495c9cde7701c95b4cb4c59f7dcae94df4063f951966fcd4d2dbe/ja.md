```
up(port::Int = Genie.config.server_port, host::String = Genie.config.server_host;
    ws_port::Int = Genie.config.websockets_port, async::Bool = ! Genie.config.run_as_server) :: Nothing
```

ウェブサーバーを起動します。`Server.up`のエイリアスです。

# 引数

  * `port::Int`: ウェブサーバーが使用するポート
  * `host::String`: ウェブサーバーが使用するホスト
  * `ws_port::Int`: Web Socketsサーバーが使用するポート
  * `async::Bool`: ウェブサーバータスクを非同期に実行する

# 例

```julia-repl
julia> up(8000, "127.0.0.1", async = false)
[ Info: Ready!
Web Server starting at http://127.0.0.1:8000
```
