```
SymmetricRankOneOperator(u) -> A
```

yields the symmetric rank one operator `A = u⋅u'` defined by the *vector* `u` and behaving as follows:

```
A'*x -> A*x
A*x  -> vscale(vdot(u, x)), u)
```

See also: [`RankOneOperator`](@ref), [`LinearMapping`](@ref),           [`Trait`](@ref) [`apply!`](@ref), [`vcreate`](@ref).
