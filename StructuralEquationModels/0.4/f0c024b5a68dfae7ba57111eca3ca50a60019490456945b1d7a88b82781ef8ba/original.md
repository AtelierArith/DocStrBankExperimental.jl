`EnsembleParameterTable`s contain the specification of an ensemble structural equation model.

# Constructor

```
(1) EnsembleParameterTable(graph; observed_vars, latent_vars, groups)

(2) EnsembleParameterTable(ps::Pair...; param_labels = nothing)
```

Return an `EnsembleParameterTable` constructed from (1) a graph or (2) multiple specifications.

# Arguments

  * `graph`: graph defined via `@StenoGraph`
  * `observed_vars::Vector{Symbol}`: observed variable names
  * `latent_vars::Vector{Symbol}`: latent variable names
  * `param_labels::Vector{Symbol}`: (optional) a vector of parameter names
  * `ps::Pair...`: `:group_name => specification`, where `specification` is either a `ParameterTable` or `RAMMatrices`

# Examples

See the online documentation on [Multigroup models](@ref).
