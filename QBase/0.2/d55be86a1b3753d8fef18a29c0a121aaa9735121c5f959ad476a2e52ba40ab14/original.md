Computes the outcome probabilities for a quantum measurement. The conditional probabilities are determined by the Born rule, $P(i|j) = \text{Tr}[\Pi_i \rho_j]$, where $\Pi_j$ is a POVM element and $\rho_j$ is a density matrix.

Measurement of a single `Ket` or  `State`:

```
measure(Π :: POVM, ρ :: State) :: Probabilities
measure(Π :: POVM, ψ :: Ket) :: Probabilities
measure(Π :: PVM, ρ :: State) :: Probabilities
measure(Π :: PVM, ψ :: Ket) :: Probabilities
```

Measurement of an ensemble of `Ket` or `State` types:

```
measure(Π :: POVM, ρ_states :: Vector{<:State}) :: Conditionals
measure(Π :: POVM, ψ_kets :: Vector{<:Ket}) :: Conditionals
measure(Π :: PVM, ρ_states :: Vector{<:State}) :: Conditionals
measure(Π :: PVM, ψ_kets :: Vector{<:Ket}) :: Conditionals
```
