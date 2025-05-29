```
eigenenergies(A::QuantumObject; sparse::Bool=false, kwargs...)
```

Calculate the eigenenergies

# Arguments

  * `A::QuantumObject`: the [`QuantumObject`](@ref) to solve eigenvalues
  * `sparse::Bool`: if `false` call [`eigvals(A::QuantumObject; kwargs...)`](@ref), otherwise call [`eigsolve`](@ref). Default to `false`.
  * `kwargs`: Additional keyword arguments passed to the solver. If `sparse=true`, the keyword arguments are passed to [`eigsolve`](@ref), otherwise to [`eigen`](@ref).

# Returns

  * `::Vector{<:Number}`: a list of eigenvalues
