```
emit(server::WebsocketServer, data::Union{Array{UInt8,1}, String, Number})
```

指定された `data` をサーバーに接続されているすべてのクライアントにメッセージとして送信します。

# 例

```julia
emit(server, "Hello everybody from your loving server.")
```
