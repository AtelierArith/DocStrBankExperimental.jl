```
erasure_channel( ρ :: State, μ :: Real ) :: State
```

The erasure channel mixes a quantum state `ρ` with an error flag $|F\rangle$ orthogonal to the Hilbert space of `ρ`. The argument `μ` describes the probability that `ρ` is replaced with the error flag. For a quantum state $\rho$, the erasure channel is expressed:

$$
    \mathcal{E}_{\mu}(\rho) = \mu \rho + (1 - \mu) |F \rangle \langle F|
$$

Note that the erasure channel increases the dimension of the Hilbert space by 1.

A `DomainError` is thrown if `μ` does not satisfy `1 ≥ μ ≥ 0`.
