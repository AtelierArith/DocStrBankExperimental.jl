```
solve!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}, iteration::Int; interpolationorder::Int=1)
```

Refine the `MDBM_Problem` `iteration` times, then perform a neighbour check. `interpolationorder` defines the interpolation method within the n-cubes.

# Examples

```julia
julia> solve!(mymdbm,4)
```
