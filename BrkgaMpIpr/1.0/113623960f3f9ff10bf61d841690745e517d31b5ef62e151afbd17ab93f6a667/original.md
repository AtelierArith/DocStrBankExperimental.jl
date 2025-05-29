```
parse(::Type{PathRelinkingType}, value::String)::PathRelinkingType
```

Parse `value` returning a valid [`PathRelinkingType`](@ref) enumeration.

# Throws

  * `ArgumentError`: in case the type description does not match.
