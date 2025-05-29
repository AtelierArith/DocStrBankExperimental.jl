```
eigenstates(A::QuantumObject; sparse::Bool=false, kwargs...)
```

Calculate the eigenvalues and corresponding eigenvectors

# Arguments

  * `A::QuantumObject`: the [`QuantumObject`](@ref) to solve eigenvalues and eigenvectors
  * `sparse::Bool`: if `false` call [`eigen(A::QuantumObject; kwargs...)`](@ref), otherwise call [`eigsolve`](@ref). Default to `false`.
  * `kwargs`: Additional keyword arguments passed to the solver. If `sparse=true`, the keyword arguments are passed to [`eigsolve`](@ref), otherwise to [`eigen`](@ref).

# Returns

  * `::EigsolveResult`: containing the eigenvalues, the eigenvectors, and some information from the solver. see also [`EigsolveResult`](@ref)
