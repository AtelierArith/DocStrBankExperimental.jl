```
choi_evolve(Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number}) :: Matrix
choi_evolve(
    Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number}, dims :: Vector{Int}
) :: Matrix
```

Applies the Choi operator `Λ` to the density operator `ρ` where `dims = [dim_in, dim_out]` describes the input and output dimension of the Choi operator `Λ`. The output of the quantum channel evaluated as,

$$
    \rho'_B = \text{Tr}_A[\Lambda_{AB}(\rho_A^{T}\otimes \mathbb{I}_B)],
$$

where the [`partial_trace`](@ref) is taken with respect to the input system.

!!! warning "Dimension Verification"
    The method `choi_evolve(Λ :: Matrix{<:Number}, ρ :: Matrix{<:Number})` does not verify the dimensions of `Λ` or `ρ`. An error will occur if proper dimensions are not used. This function bypasses the QBase.jl type system and relies upon the user to verify their arguments.

