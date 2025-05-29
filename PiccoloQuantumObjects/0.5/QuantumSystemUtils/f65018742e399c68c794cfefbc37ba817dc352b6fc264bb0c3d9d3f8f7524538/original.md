```
is_reachable(gate, hamiltonians; kwargs...)
```

Check if the `gate` is reachable using the given `hamiltonians`.

# Arguments

  * `gate::AbstractMatrix`: target gate
  * `hamiltonians::AbstractVector{<:AbstractMatrix}`: generators of the Lie algebra

# Keyword Arguments

  * `subspace::AbstractVector{<:Int}=1:size(gate, 1)`: subspace indices
  * `compute_basis::Bool=true`: compute the basis or use the Hamiltonians directly
  * `remove_trace::Bool=true`: remove trace from generators
  * `verbose::Bool=true`: print information about the operator algebra
  * `atol::Float32=eps(Float32)`: absolute tolerance

See also [`QuantumSystemUtils.operator_algebra`](@ref).
