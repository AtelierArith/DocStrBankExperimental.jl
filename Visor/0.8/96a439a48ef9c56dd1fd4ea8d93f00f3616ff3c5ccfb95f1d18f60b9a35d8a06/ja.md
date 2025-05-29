```
call(name::String, request::Any; timeout::Real=3)
```

フル `name` で識別されるプロセスに `request` を送信し、応答を待ちます。

`timeout` が -1 の場合は無限に待機します。それ以外の場合、`timeout` 秒以内に応答が受信されないと `ErrorException` が発生します。

ターゲットタスクに送信されるメッセージは、リクエストと応答を返すためのチャネルを含む `Request` 構造体です。

```julia
using Visor

function server(task)
    for msg in task.inbox
        isshutdown(msg) && break
        put!(msg.inbox, msg.request * 2)
    end
    println("server done")
end

function requestor(task)
    request = 10
    response = call("server", request)
    println("server(",request,")=",response)
    shutdown()
end

supervise([process(server), process(requestor)])
```
