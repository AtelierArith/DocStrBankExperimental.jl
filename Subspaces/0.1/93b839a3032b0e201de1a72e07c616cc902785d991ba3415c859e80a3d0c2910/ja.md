```julia
variable_in_space(
    S::Subspaces.Subspace{<:Real, N}
) -> Union{Convex.MultiplyAtom, Convex.ReshapeAtom}

```

指定された部分空間にわたる `Convex.jl` 変数を作成します。
