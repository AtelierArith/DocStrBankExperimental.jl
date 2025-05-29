```
WebSockets.serve(server::ServerWS, port)
WebSockets.serve(server::ServerWS, host, port)
WebSockets.serve(server::ServerWS, host, port, verbose)
```

WebSockets.HTTP.listenのための高レベルインターフェースです。serveを非同期で実行している場合、close(ServerWS)を呼び出すとserveタスクは終了します。

キャッチされたエラーとスタックトレースはserver.outチャネルに出力されます。server.inチャネルはclose(ServerWS)によって使用されます。

# 例

```julia
    @async WebSockets.serve(myserver_WS, "127.0.0.1", 8080)
```

接続タスクの失敗が疑われる場合：

```julia
    if isready(myserver_WS.out)
        stack_trace = take!(myserver_WS.out)
    end
```
