`readguarded(websocket) => (Vector, Bool)`

返す (data::Vector, true) または (Vector{UInt8}(), false)

ピアはいつでも切断する可能性がありますが、原因に関係なく、通常は書き込めない場合にウェブソケット処理関数を終了したいだけです。

例えば：

```julia
while true
    data, success = readguarded(websocket)
    !success && break
    println(String(data))
end
```

エラーを確認するには（もしあれば）、一時的にログの最小レベルをLogging.debugに設定します。例えば：

```julia
using WebSockets, Logging
global_logger(WebSocketLogger(stderr, Logging.Debug));
```
