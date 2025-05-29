```
parse(::Type{BiasFunction}, value::String)::BiasFunction
```

Parse `value` returning a valid [`BiasFunction`](@ref) enumeration.

# Throws

  * `ArgumentError`: in case the bias description does not match.
