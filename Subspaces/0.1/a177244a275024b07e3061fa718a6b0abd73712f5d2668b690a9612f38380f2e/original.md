```julia
projection(
    S::Subspaces.Subspace{<:Number, N},
    x::Convex.AbstractExpr
) -> Union{Convex.MultiplyAtom, Convex.ReshapeAtom}

```

Projection of vector `x` onto suspace `S`.
