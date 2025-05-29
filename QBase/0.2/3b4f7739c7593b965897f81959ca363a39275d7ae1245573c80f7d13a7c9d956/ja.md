```
error_probability(
    priors::AbstractVector,
    ρ_states::Vector{<:AbstractMatrix},
    Π::AbstractVector{<:AbstractMatrix}
) :: Float64
```

指定されたPOVMを使用して量子状態を誤って区別する確率。この量は単純に$P_{\text{Error}} = 1 - P_{\text{Success}}$として得られます。
