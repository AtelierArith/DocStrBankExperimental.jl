```
entanglement(ρ::QuantumObject, sel; kwargs...)
```

Calculates the [entanglement entropy](https://en.wikipedia.org/wiki/Entropy_of_entanglement) by doing the partial trace of `ρ`, selecting only the dimensions with the indices contained in the `sel` vector, and then use the Von Neumann entropy [`entropy_vn`](@ref).

# Notes

  * `ρ` can be either a [`Ket`](@ref) or an [`Operator`](@ref). But should be a pure state.
  * `sel` specifies the indices of the remaining sub-system. See also [`ptrace`](@ref).
  * `kwargs` are the keyword arguments for calculating Von Neumann entropy. See also [`entropy_vn`](@ref).
