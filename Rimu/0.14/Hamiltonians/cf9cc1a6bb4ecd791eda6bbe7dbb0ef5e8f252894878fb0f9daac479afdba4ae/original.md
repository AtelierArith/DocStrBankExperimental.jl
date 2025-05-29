```
Stoquastic(ham <: AbstractHamiltonian) <: AbstractHamiltonian
```

A wrapper for an [`AbstractHamiltonian`](@ref) that replaces all off-diagonal matrix elements `v` by `-abs(v)`, thus making the new Hamiltonian *stoquastic*.

A stoquastic Hamiltonian does not have a Monte Carlo sign problem. For a hermitian `ham` the smallest eigenvalue of `Stoquastic(ham)` is ≤ the smallest eigenvalue of `ham`.
