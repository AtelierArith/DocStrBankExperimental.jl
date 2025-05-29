```
OrbitStateVector(t::Tepoch, r::AbstractVector{Tr}, v::AbstractVector{Tv}[, a::AbstractVector{Ta}])
```

Create an orbit state vector with epoch `t` [Julian Day], position `r` [m], velocity `v` [m / s], and acceleration `a` [m / s²]. If the latter is omitted, it will be filled with `[0, 0, 0]`.

The object type is obtained by promoting `Tr`, `Tv`, and `Ta`.
