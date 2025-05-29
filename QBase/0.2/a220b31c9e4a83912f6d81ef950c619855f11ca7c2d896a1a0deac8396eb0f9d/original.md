```
KrausChannel(
    kraus_ops :: Vector{Matrix{T}};
    atol=ATOL :: Float64
) :: KrausChannel{T}
```

The Kraus operator representation of a quantum channel. The channel evolves a density operator $\rho$ as,

$$
    \mathcal{N}(\rho) = \sum_{i} K_{i} \rho K_{i}^{\dagger},
$$

where $\{K_i \in L(A,B)\}_i$ are a set of linear operators known as Kraus operators.

A `DomainError` is thrown if `kraus_ops` do not constitute a quantum channel. See [`is_kraus_channel`](@ref) for details.
