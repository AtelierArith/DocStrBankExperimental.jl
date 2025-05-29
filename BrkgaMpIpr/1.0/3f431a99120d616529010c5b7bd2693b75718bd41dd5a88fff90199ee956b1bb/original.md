```
parse(::Type{PathRelinkingSelection}, value::String)::PathRelinkingSelection
```

Parse `value` returning a valid [`PathRelinkingSelection`](@ref) enumeration.

# Throws

  * `ArgumentError`: in case the selection description does not match.
