`writeguarded(websocket, message) => Bool`

書き込みが成功した場合はtrueを返し、そうでない場合はfalseを返します。ピアはいつでも切断する可能性がありますが、原因に関係なく、書き込みができない場合は通常、ウェブソケット処理関数を終了したいと思うでしょう。

エラーを確認するには（もしあれば）、一時的にログの最小レベルをLogging.debugに設定します。例えば：

```julia
using WebSockets, Logging
global_logger(WebSocketLogger(stderr, Logging.Debug));
```
