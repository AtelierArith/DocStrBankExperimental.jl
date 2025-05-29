```
notyettreated(e, ecut, c::ParallelCondition, s::ParallelStrength)
notyettreated(e, ecut=e; c=Unconditional(), s=Exact())
```

Construct a [`NotYetTreatedParallel`](@ref) with fields set by the arguments. By default, `c` is set as [`Unconditional()`](@ref) and `s` is set as [`Exact()`](@ref). When working with `@formula`, a wrapper method of `notyettreated` calls this method.

# Examples

```jldoctest; setup = :(using DiffinDiffsBase)
julia> notyettreated(5)
Parallel trends with any not-yet-treated group:
  Not-yet-treated groups: 5
  Treated since: 5

julia> typeof(notyettreated(5))
NotYetTreatedParallel{Unconditional,Exact}

julia> notyettreated([-1, 5, 6], 5)
Parallel trends with any not-yet-treated group:
  Not-yet-treated groups: -1, 5, 6
  Treated since: 5

julia> notyettreated([4, 5, 6], [4, 5, 6])
Parallel trends with any not-yet-treated group:
  Not-yet-treated groups: 4, 5, 6
  Treated since: 4, 5, 6
```
