```
Limit{T}(x, s)
```

The Limit type represents endpoints of closed and open intervals.  The val field is the value of the endpoint.  The sign field is used to represent the openness/closedness of the interval endpoint, using an Infinitesmal.

```jl-doctest julia> limit(1.0) 1.0+0

julia> plus_eps(1.0) 1.0+ϵ

julia> minus_eps(1.0) 1.0-ϵ

julia> plus*eps(1.0) + minus*eps(1.0) 2.0+0.0

julia> plus_eps(1.0) * 2 2.0+2.0ϵ

julia> plus*eps(1.0) * minus*eps(1.0) 1.0-1.0ϵ

julia> plus*eps(-1.0) * minus*eps(1.0) -1.0+2.0ϵ

julia> 1.0 < plus_eps(1.0) true

julia> 1.0 < minus_eps(1.0) false
