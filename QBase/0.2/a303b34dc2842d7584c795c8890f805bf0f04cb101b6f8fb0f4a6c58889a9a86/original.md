```
shannon_entropy( probabilities :: AbstractVector ) :: Float64
```

The classical entropy of a probability distribution:

$$
S = -\sum_{i=1}^n p_i \log_2(p_i)
$$

A `DomainError` is thrown if input `probabilities` does not satisfy [`is_probability_distribution`](@ref).
