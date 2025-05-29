```
kraus_evolve(
    kraus_ops :: Vector{<:AbstractMatrix},
    ρ :: Matrix
) :: Matrix
```

Applies the Kraus operators `kraus_ops` to evolve the density operator `ho`. The evolved state $\rho'$ is constructed as,

$$
    \rho' = \sum_{i} K_{i} \rho K_{i}^{\dagger}
$$

where $K_i$ is a Kraus operator.
