```julia
frombasis(
    S::Subspaces.Subspace{<:Number, 1},
    x::Convex.AbstractExpr
) -> Convex.MultiplyAtom

```

Returns a vector from the given basis components in the basis `S.basis`.
