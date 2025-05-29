```
success_probability(
    priors::AbstractVector,
    states::Vector{<:AbstractMatrix},
    Π::Vector{<:AbstractMatrix}
) :: Float64
```

指定されたPOVMで量子状態を正しく区別する確率:

$$
P_{\text{Success}} = \sum_{i=1}^n p_i \text{Tr}[\Pi_i \rho_i].
$$

状態の数はPOVMの数と一致する必要があります。
