`ParameterTable`s contain the specification of a structural equation model.

# Constructor

```
(1) ParameterTable(graph; observed_vars, latent_vars, ...)

(2) ParameterTable(ram_matrices; ...)
```

Return a `ParameterTable` constructed from (1) a graph or (2) RAM matrices.

# Arguments

  * `graph`: graph defined via `@StenoGraph`
  * `observed_vars::Vector{Symbol}`: observed variable names
  * `latent_vars::Vector{Symbol}`: latent variable names
  * `ram_matrices::RAMMatrices`: a `RAMMatrices` object

# Examples

See the online documentation on [Model specification](@ref) and the [Graph interface](@ref).

# Extended help

## Additional keyword arguments

  * `parname::Symbol = :θ`: prefix for automatically generated parameter labels
