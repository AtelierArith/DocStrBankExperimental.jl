```
replacer_channel(
    ρ :: State,
    σ :: State,
    μ :: Real
) :: State
```

The replacer channel replaces the quantum state `ρ` with quantum state `σ` with probability `μ`. The replacer channel is expressed:

$$
    \mathcal{R}_{\mu}(\rho) = \mu \rho + (1-\mu)\sigma
$$

A `DomainError` is thrown if

  * `μ` does not satisfy `1 ≥ μ ≥ 0`
  * `ρ` and `σ` are not the same size
