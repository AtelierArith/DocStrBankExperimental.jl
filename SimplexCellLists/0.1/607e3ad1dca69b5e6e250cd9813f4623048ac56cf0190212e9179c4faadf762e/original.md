Abstract type for all SimplexCellList implementations.

Implementations must have a constructor with signature like

```julia
T(numpointgroups::Integer, numlinegroups::Integer, numtrianglegroups::Integer; kwargs...)::T
```

Where `numpointgroups` is the number of groups of points, `numlinegroups` is the number of groups of lines, and `numtrianglegroups` is the number of groups of triangles.

`kwargs` are options specific for `T`
