```julia
projectZrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

Project `qubit` of `state` along the Z axis and randomize the phase if necessary.

Lower boilerplate version of [`project!`](@ref).

See also: [`project!`](@ref), [`projectZ!`](@ref), [`projectXrand!`](@ref), [`projectYrand!`](@ref)
