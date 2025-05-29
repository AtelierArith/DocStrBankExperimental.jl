```
axesextend!(mdbm::MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT,aT}, axisnumber::Integer; prepend::AbstractArray=[], append::AbstractArray=[])
```

Extend parameter space of the selected Axis by prepend and append the grid.

Note, that the resolution and the monotonically is not checked.

# Examples

extending the second parameter of the mdbm problem:

```jldoctest
julia> axesextend!(mymdbm,2,prepend=-6.2:0.05:-2.2,append=2.2:0.2:3);
```
