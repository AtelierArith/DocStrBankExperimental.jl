```julia
projection(
    S::Subspaces.Subspace{<:Number, N},
    x::Convex.AbstractExpr
) -> Union{Convex.MultiplyAtom, Convex.ReshapeAtom}

```

ベクトル `x` を部分空間 `S` に射影します。
