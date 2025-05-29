```
to_numeric(q::QNumber, b::QuantumOpticsBase.Basis; level_map = nothing)
to_numeric(q::QNumber, state; level_map = nothing)
```

Convert a symbolic operator `q` to its equivalent numeric (matrix) form on the basis `b`. The optional argument `level_map` can be set to a dictionary that specifies how to map levels of a [`Transition`](@ref) to the ones given in an `NLevelBasis`. **Note:** If the levels of a transition are symbolic, setting `level_map` is required.

See also: [`numeric_average`](@ref), [`initial_values`](@ref)

# Examples

julia> to_numeric(Destroy(FockSpace(:fock), :a), FockBasis(10)) Operator(dim=11x11)   basis: Fock(cutoff=10)[...]
