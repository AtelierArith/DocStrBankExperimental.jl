```
depolarizing_channel( ρ :: State, μ :: Real ) :: State
```

The depolarizing channel mixes uniform classical noise into a quantum state `ρ`. The argument `μ` describes the amount of noise mixed into the quantum states. For a quantum state $\rho$, the depolarizing channel is expressed:

$$
    \mathcal{D}_{\mu}(\rho) = \mu \rho + \frac{(1 - \mu)}{d}\mathbb{I}_d
$$

A `DomainError` is thrown if `μ` does not satisfy `1 ≥ μ ≥ 0`.
