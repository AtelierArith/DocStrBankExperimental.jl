`PermX(W::ComplexReflectionGroup,M::AbstractMatrix)`

Let `M` be an invertible linear map of the reflection representation of `W` which  preserves the set  of roots of  `parent(W)`, and normalizes `W` (for the  action of  matrices on  the right).  `PermX` returns the corresponding permutation  of the roots of `parent(W)`;  it returns `nothing` if `M` does not normalize the set of roots of `parent(W)`.

```julia-repl
julia> W=reflection_subgroup(rootdatum("E7sc"),1:6)
E₇₍₁₂₃₄₅₆₎=E₆Φ₁

julia> PermX(W,reflrep(W,longest(W)))==longest(W)
true
```
