```julia
frombasis(
    S::Subspaces.Subspace{<:Number, 2},
    x::Convex.AbstractExpr
) -> Convex.ReshapeAtom

```

与えられた基底成分から、基底 `S.basis` におけるベクトルを返します。
