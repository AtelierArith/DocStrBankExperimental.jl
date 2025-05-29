```julia
frombasis(
    S::Subspaces.Subspace{<:Number, 2},
    x::Convex.AbstractExpr
) -> Convex.ReshapeAtom

```

Returns a vector from the given basis components in the basis `S.basis`.
