```
apply(A::MPO, x::MPS; kwargs...)
```

Contract the `MPO` `A` with the `MPS` `x` and then map the prime level of the resulting MPS back to 0.

Equivalent to `replaceprime(contract(A, x; kwargs...), 2 => 1)`.

See also [`contract`](@ref) for details about the arguments available.
