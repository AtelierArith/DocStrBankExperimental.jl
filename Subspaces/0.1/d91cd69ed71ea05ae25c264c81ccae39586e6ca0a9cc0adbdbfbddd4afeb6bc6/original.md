```julia
tobasis(
    S::Subspaces.Subspace{<:Number, N},
    x::Convex.AbstractExpr
) -> Convex.MultiplyAtom

```

Returns the basis components of `x` in the basis `S.basis`.
