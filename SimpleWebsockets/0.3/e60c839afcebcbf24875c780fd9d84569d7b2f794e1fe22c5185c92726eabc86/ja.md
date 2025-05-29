```
send(ws::WebsocketConnection, data::Union{String, Number, Array{UInt8,1}})
```

指定された `data` をメッセージとしてワイヤー越しに送信します。
