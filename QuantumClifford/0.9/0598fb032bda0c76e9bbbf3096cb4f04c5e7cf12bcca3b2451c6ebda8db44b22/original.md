```julia
projectYrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

Project `qubit` of `state` along the Y axis and randomize the phase if necessary.

Lower boilerplate version of [`project!`](@ref).

See also: [`project!`](@ref), [`projectY!`](@ref), [`projectXrand!`](@ref), [`projectZrand!`](@ref)
