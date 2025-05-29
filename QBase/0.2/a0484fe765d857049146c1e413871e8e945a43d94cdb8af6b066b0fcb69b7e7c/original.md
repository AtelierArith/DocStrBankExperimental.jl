```
is_probability_distribution(
    probabilities :: Vector{<:Real};
    atol=ATOL :: Float64
) :: Bool
```

Returns `true` if the provided vector is a valid probability distribution:

  * `sum(probabilities) ≈ 1`
  * `probabilities[i] ≥ 0 ∀ i`
