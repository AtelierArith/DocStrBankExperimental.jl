```
mixed_state(
    priors :: Probabilities,
    states :: Vector{<:State};
    atol=ATOL :: Float64
) :: State
```

量子状態の統計的混合（加重平均）を構築します。このメソッドは、[`is_probability_distribution`](@ref)および[`is_density_matrix`](@ref)の要件を満たす`Vector`および`Matrix`タイプにも使用できます。

```julia
mixed_state(
    priors :: AbstractVector,
    states :: Vector{<:AbstractMatrix}
) :: State
```

提供された`Vector`の`priors`または`states`がそれぞれの要件を満たさない場合、`DomainError`がスローされます。
