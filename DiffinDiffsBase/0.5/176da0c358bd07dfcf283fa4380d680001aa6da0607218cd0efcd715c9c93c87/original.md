```
nevertreated(e, c::ParallelCondition, s::ParallelStrength)
nevertreated(e; c=Unconditional(), s=Exact())
```

Construct a [`NeverTreatedParallel`](@ref) with fields set by the arguments. By default, `c` is set as [`Unconditional()`](@ref) and `s` is set as [`Exact()`](@ref). When working with `@formula`, a wrapper method of `nevertreated` calls this method.

# Examples

```jldoctest; setup = :(using DiffinDiffsBase)
julia> nevertreated(-1)
Parallel trends with any never-treated group:
  Never-treated groups: -1

julia> typeof(nevertreated(-1))
NeverTreatedParallel{Unconditional,Exact}

julia> nevertreated([-1, 0])
Parallel trends with any never-treated group:
  Never-treated groups: -1, 0

julia> nevertreated([-1, 0]) == nevertreated(-1:0) == nevertreated(Set([-1, 0]))
true
```
