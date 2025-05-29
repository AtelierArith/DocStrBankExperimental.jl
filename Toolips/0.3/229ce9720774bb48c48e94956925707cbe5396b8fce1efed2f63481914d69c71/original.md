```julia
get_method(c::AbstractConnection) -> ::String
```

Gets the `METHOD` of the incoming `HTTP` request. The *METHOD* is what type of  HTTP request the client is trying to send; `POST` or `GET`. 

```example
module MyServer
using Toolips

logger = Toolips.Logger()

home = route("/") do c::Connection
    @info "a get request?: " * string(get_method(c) == "GET")
end

export home, logger
end
```
