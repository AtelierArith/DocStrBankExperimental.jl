```julia
Routes{T} (Type Alias for Vector{T} where T <:AbstractRoute)
```

`Routes` are simple one-dimensional vectors of routes. Using multiple dispatch, these  vectors effectively become routers and can be extended using multiple dispatch.  To change individual `Route` functionality, view `Route` and `MultiRoute`, dispatching `Routes{T <: Any}`  to `route!(c::AbstractConnection, r::Routes{T <: Any})` will create a new router, which is intended to call  `route!` on routes.

```example

```

  * See also: `AbstractConnection`, `Route`, `route`, `route!`
