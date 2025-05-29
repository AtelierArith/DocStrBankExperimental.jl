```
layer(v)
```

Return the computation wrapped inside `v` and inside any mutable wrappers.

# Examples

```jldoctest
julia> using NaiveNASflux, Flux

julia> layer(fluxvertex(Dense(2,3), inputvertex("in", 2)))
Dense(2 => 3)       # 9 parameters
```
