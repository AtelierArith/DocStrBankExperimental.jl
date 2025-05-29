`target(request) => String`

アップグレードリクエストターゲットを読み取るための便利な関数。例えば：

```julia
    function gatekeeper(req, ws)
        if target(req) == "/gamepad"
            @spawnat 2 gamepad(ws)
        elseif target(req) == "/console"
            @spawnat 3 console(ws)
            ...
        end
    end
```

次に、ブラウザのJavaScript（またはJulia WebSockets.open( , )と同等のもの）で：

```javascript
function load(){
    var wsuri = document.URL.replace("http:", "ws:");
    ws1 = new WebSocket(wsuri + "/gamepad");
    ws2 = new WebSocket(wsuri + "/console");
    ws3 = new WebSocket(wsuri + "/graphics");
    ws4 = new WebSocket(wsuri + "/audiochat");
    ws1.onmessage = function(e){vibrate(e.data)}
    } // load

```
