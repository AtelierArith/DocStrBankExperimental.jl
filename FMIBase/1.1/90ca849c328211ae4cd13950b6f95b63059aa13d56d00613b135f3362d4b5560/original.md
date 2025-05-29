```
getModelIdentifier(md::fmiModelDescription; type=nothing)
```

Returns the tag 'modelIdentifier' from CS or ME section.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Keywords

  * `type=nothing`: Defines whether a Co-Simulation or Model Exchange is present. (default = nothing)

# Returns

  * `md.modelExchange.modelIdentifier::String`: Returns the tag `modelIdentifier` from ModelExchange section.
  * `md.coSimulation.modelIdentifier::String`: Returns the tag `modelIdentifier` from CoSimulation section.
