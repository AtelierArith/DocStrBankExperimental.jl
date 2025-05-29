`subprotocol(request) => String`

アップグレードリクエストのサブプロトコルを読み取るための便利な関数です。受け入れ可能なサブプロトコルは、addsubproto(myprotocol)を使用して事前に定義する必要があります。他のサブプロトコルはハンドシェイクを通過しません。例えば：

```julia
WebSockets.addsubproto("instructions")
WebSockets.addsubproto("relay_backend")
function gatekeeper(req, ws)
    subpr = WebSockets.subprotocol(req)
    if subpr == "instructions"
        instructions(ws)
    elseif subpr == "relay_backend"
        relay_backend(ws)
    end
end
```

次に、ブラウザのJavaScript（またはJulia WebSockets.open( , )と同等のもの）で：

```javascript
function load(){
    var wsuri = document.URL.replace("http:", "ws:");
    ws1 = new WebSocket(wsuri, "instructions");
    ws2 = new WebSocket(wsuri, "relay_backend");
    ws1.onmessage = function(e){doinstructions(e.data)};
    ...
    } // load
```
