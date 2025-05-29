```
OpenQuantumSystem <: AbstractQuantumSystem
```

A struct for storing open quantum dynamics and the appropriate gradients.

# Additional fields

  * `dissipation_operators::Vector{AbstractMatrix}`: The dissipation operators.

See also [`QuantumSystem`](@ref).

# Constructors

  * OpenQuantumSystem(       H*drift::AbstractMatrix{<:Number},       H*drives::AbstractVector{<:AbstractMatrix{<:Number}}       dissipation_operators::AbstractVector{<:AbstractMatrix{<:Number}};       kwargs...   )
  * OpenQuantumSystem(       H*drift::Matrix{<:Number}, H*drives::AbstractVector{Matrix{<:Number}};       dissipation_operators::AbstractVector{<:AbstractMatrix{<:Number}}=Matrix{ComplexF64}[],       kwargs...   )
  * OpenQuantumSystem(H_drift::Matrix{<:Number}; kwargs...)
  * OpenQuantumSystem(H_drives::Vector{Matrix{<:Number}}; kwargs...)
  * OpenQuantumSystem(H::Function, n_drives::Int; kwargs...)
