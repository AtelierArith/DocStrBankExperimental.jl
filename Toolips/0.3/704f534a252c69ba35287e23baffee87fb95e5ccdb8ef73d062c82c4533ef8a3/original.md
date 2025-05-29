```julia
get_host(c::AbstractConnection) -> ::String
```

Gets the host (domain name and TLD) the client is currently requesting. The example below is pulled directly from  [`ChiProxy`](https://github.com/ChifiSource/ChiProxy.jl). This is a `Toolips`-based  proxy server, which uses a router based on the hostname, rather than the target.  By extending `route!` to alter behavior with proxy routes, this example uses `get_host`  to determine the active path, rather than `get_route`.

```example
using Toolips
import Toolips: route!
route!(c::Connection, vec::Vector{<:AbstractProxyRoute}) = begin
    if Toolips.get_route(c) == "/favicon.ico"
        write!(c, "no icon here, fool")
        return
    end
    selected_route::String = get_host(c)
    if selected_route in vec
        route!(c, vec[selected_route])
    else
        write!(c, "this route is not here")
    end
end
```
