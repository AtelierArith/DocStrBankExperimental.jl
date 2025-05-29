`RAMMatrices` contain the specification of a structural equation model.

# Constructor

```
(1) RAMMatrices(partable::ParameterTable; param_labels = nothing)

(2) RAMMatrices(;A, S, F, M = nothing, param_labels, vars = nothing)

(3) RAMMatrices(partable::EnsembleParameterTable)
```

Return `RAMMatrices` constructed from (1) a parameter table or (2) individual matrices.

(3) Return a dictionary of `RAMMatrices` from an `EnsembleParameterTable` (keys are the group names).

# Arguments

  * `partable`
  * `A`: matrix of directed effects
  * `S`: matrix of undirected effects
  * `F`: filter matrix
  * `M`: vector of mean effects
  * `param_labels::Vector{Symbol}`: parameter labels
  * `vars::Vector{Symbol}`: variable names corresponding to the A, S and F matrix columns

# Examples

See the online documentation on [Model specification](@ref) and the [RAMMatrices interface](@ref).
