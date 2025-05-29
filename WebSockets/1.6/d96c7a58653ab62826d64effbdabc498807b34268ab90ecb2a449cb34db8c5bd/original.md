`subprotocol(request) => String`

Convenience function for reading upgrade request subprotocol. Acceptable subprotocols need to be predefined using addsubproto(myprotocol). No other subprotocols will pass the handshake. E.g.

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

Then, in browser javascript (or equivalent with Julia WebSockets.open( , ))

```javascript
function load(){
    var wsuri = document.URL.replace("http:", "ws:");
    ws1 = new WebSocket(wsuri, "instructions");
    ws2 = new WebSocket(wsuri, "relay_backend");
    ws1.onmessage = function(e){doinstructions(e.data)};
    ...
    } // load
```
