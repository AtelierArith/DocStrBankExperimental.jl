```
getVariableNamingConvention(md::fmi2ModelDescription)
```

Returns the tag 'varaiblenamingconvention' from the model description.

# Arguments

  * `md::fmi2ModelDescription`: Struct which provides the static information of ModelVariables.

# Returns

  * `md.variableNamingConvention::Union{fmi2VariableNamingConvention, Nothing}`: Returns the tag 'variableNamingConvention' from the model description.
