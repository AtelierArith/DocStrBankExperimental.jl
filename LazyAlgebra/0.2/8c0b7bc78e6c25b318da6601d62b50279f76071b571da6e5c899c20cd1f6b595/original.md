```
RankOneOperator(u, v) -> A
```

yields the rank one linear operator `A = u⋅v'` defined by the two *vectors* `u` and `v` and behaving as:

```
A*x  -> vscale(vdot(v, x)), u)
A'*x -> vscale(vdot(u, x)), v)
```

See also: [`SymmetricRankOneOperator`](@ref), [`LinearMapping`](@ref),           [`apply!`](@ref), [`vcreate`](@ref).
