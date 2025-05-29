```julia
route!(c::AbstractConnection, r::AbstractRoute) -> ::Nothing
route!(c::Connection, tr::Routes{<:AbstractRoute}) -> ::Nothing
```

The `route!` `Function` is used by the router twice; once when the entire  `Vector` of routes is routed (the second method listed above,) and again  on the `Route` that is routed to. Considering this, it is possible to create a new  router by extending `route!(c::Connection, tr::Routes{<:AbstractRoute})` The following example is pulled from [`ChiProxy`](https://github.com/ChifiSource/ChiProxy.jl),  this example creates a router based on hostname, and also changes route functionality  to perform a proxy pass.

```julia
using Toolips
import Toolips: route!

function route!(c::Toolips.AbstractConnection, pr::AbstractProxyRoute)
    Toolips.proxy_pass!(c, "http://$(string(pr.ip4))")
end

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

  * See also: `multiroute!`, `route!`, `Route`, `Routes`, `Connection`, `AbstractConnection`, `start!`
