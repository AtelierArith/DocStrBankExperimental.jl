```
is_reachable(gate::AbstractMatrix{<:Number}, system::AbstractQuantumSystem; kwargs...)
```

Check if the `gate` is reachable using the given `system`.

# Keyword Arguments

  * `use_drift::Bool=true`: include drift Hamiltonian in the generators
  * `kwargs...`: keyword arguments for `is_reachable`
