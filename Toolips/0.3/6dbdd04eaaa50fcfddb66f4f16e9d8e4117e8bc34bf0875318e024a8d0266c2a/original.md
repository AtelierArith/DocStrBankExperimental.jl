```julia
get_route(c::AbstractConnection) -> ::String
```

Gets the current target of an incoming `Connection`. (This `Function` is used  by the router to direct  incoming connections to your routes.)

```example
module MyServer
using Toolips
using Test

logger = Toolips.Logger()

home = route("/") do c::Connection
    @test get_route(c) == "/"
end

export home, logger
end
```
