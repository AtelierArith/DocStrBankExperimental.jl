```julia
tobasis(
    S::Subspaces.Subspace{<:Number, N},
    x::Convex.AbstractExpr
) -> Convex.MultiplyAtom

```

`x`の基底`S.basis`における基底成分を返します。
