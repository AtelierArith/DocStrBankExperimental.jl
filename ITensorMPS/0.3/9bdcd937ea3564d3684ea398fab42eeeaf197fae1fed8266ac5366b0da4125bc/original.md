```
apply(A::MPO, B::MPO; kwargs...)
```

Contract the `MPO` `A'` with the `MPO` `B` and then map the prime level of the resulting MPO back to having pairs of indices with prime levels of 1 and 0.

Equivalent to `replaceprime(contract(A', B; kwargs...), 2 => 1)`.

See also [`contract`](@ref) for details about the arguments available.
