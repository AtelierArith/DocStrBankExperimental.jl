```julia
proxy_pass!(c::AbstractConnection, url::String) -> ::Nothing
```

Performs a *proxy pass* – redirecting the client to another server without  performing a request, using the current server as a *proxy* to serve the other server.

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    proxy_pass!(c, "https://github.com/ChifiSource")
end

export home, logger
end
```
