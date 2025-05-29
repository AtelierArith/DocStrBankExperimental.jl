```
is_kraus_channel(
    kraus_ops :: Vector{<:AbstractMatrix};
    atol=ATOL :: Float64
) :: Bool
```

Returns `true` if the `kraus_ops` constitute a quantum channel. The requirements are:

  * Completeness, $\sum_{i} K^{\dagger}_i K_i = \mathbb{I}$.
