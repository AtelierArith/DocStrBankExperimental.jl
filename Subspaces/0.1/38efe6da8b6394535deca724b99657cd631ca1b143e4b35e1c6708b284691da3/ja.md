```julia
frombasis(
    S::Subspaces.Subspace{<:Number, 1},
    x::Convex.AbstractExpr
) -> Convex.MultiplyAtom

```

与えられた基底成分から、基底 `S.basis` におけるベクトルを返します。
