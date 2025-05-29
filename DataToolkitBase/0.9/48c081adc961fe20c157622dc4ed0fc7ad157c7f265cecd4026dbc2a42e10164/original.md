```
supportedtypes(ADT::Type{<:AbstractDataTransformer})::Vector{QualifiedType}
```

Return a list of types supported by the data transformer `ADT`.

This is used as the default value for the `type` key in the Data TOML. The list of types is dynamically generated based on the available methods for the data transformer.

In some cases, it makes sense for this to be explicitly defined for a particular transformer. 
