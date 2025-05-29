```julia
projectrand!(
    state,
    pauli
) -> Tuple{QuantumClifford.Register, Any}

```

Measure `pauli` operator on `state` and randomize the phase if necessary.

Lower boilerplate version of [`project!`](@ref).

See also: [`project!`](@ref), [`projectXrand!`](@ref), [`projectZrand!`](@ref), [`projectYrand!`](@ref)
