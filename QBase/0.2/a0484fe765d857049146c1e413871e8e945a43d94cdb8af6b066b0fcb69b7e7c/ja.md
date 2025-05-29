```
is_probability_distribution(
    probabilities :: Vector{<:Real};
    atol=ATOL :: Float64
) :: Bool
```

提供されたベクトルが有効な確率分布である場合は `true` を返します：

  * `sum(probabilities) ≈ 1`
  * `probabilities[i] ≥ 0 ∀ i`
