```julia
route(::Function{T}, path::String) -> ::Route{T}
route(r::Route{<:AbstractConnection} ...) -> ::MultiRoute{Route{<:AbstractConnection}}
```

The `route` `Function` is the routing interface for `Toolips` default routes.  `route` in most circumstances will take a *target path* and a `Function`, which  will be the handler for the `HTTP` response. This `Route`'s handler `Function`  will take some type of `AbstractConnection`, which we can also annotate to use with `MultiRoute`.

Inside of the handler, a `Connection` has data written to it with `write!`. This comes in the form  of data-types and `Servables`. `Servables` are essential structures for  building the web with HTML and files, this includes the `Component`, `File`,  `Style`, and `KeyFrames` types provided by `Toolips`.

```julia
module RoutingExample
using Toolips

desktop = route("/") do c::Connection
    write!(c, "this client is on desktop")
end

mobile = route("/") do c::MobileConnection
    write!(c, "this client is on mobile")
end

home = route(desktop, mobile)

export home
end
```

  * See also: `multiroute!`, `route!`, `Route`, `Routes`, `Connection`, `AbstractConnection`, `start!`
