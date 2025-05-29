```julia
route!(c::AbstractConnection, vec::Routes, r::AbstractMultiRoute) -> ::Nothing
```

This `route!` dispatch allows for another router to exist underneath the `route!`-based router. This `Function`      is called whenever a multi-route is routed. This is designed to be **imported** and      extended. For this, simply create your own `<:AbstractMultiRoute` based on `MultiRoute`,      and then write this `Method` for that type. The default `Toolips.MultiRoute`, for example, routes the          `Route{<:AbstractConnection}` according to the type of incoming `Connection`.

  * See also: `Route`, `Routes`, `Connection`, `AbstractConnection`, `MultiRoute`
