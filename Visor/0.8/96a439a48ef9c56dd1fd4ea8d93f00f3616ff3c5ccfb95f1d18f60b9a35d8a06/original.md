```
call(name::String, request::Any; timeout::Real=3)
```

Send a `request` to the process identified by full `name` and wait for a response.

If `timeout` is equal to -1 then waits forever, otherwise if a response is not received in `timeout` seconds an `ErrorException` is raised.

The message sent to the target task is a `Request` struct that contains the request and a channel for sending back the response.

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
