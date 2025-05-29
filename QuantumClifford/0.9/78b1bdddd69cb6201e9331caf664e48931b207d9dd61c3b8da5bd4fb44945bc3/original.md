```julia
projectXrand!(
    state,
    qubit
) -> Tuple{QuantumClifford.Register, UInt8}

```

Project `qubit` of `state` along the X axis and randomize the phase if necessary.

Lower boilerplate version of [`project!`](@ref).

See also: [`project!`](@ref), [`projectX!`](@ref), [`projectZrand!`](@ref), [`projectYrand!`](@ref)
