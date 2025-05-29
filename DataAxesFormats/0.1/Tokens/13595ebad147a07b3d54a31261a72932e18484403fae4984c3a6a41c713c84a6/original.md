```
unescape_value(escaped::AbstractString)::String
```

Undo [`escape_value`](@ref), that is, given an `escaped` value with a `\` characters escaping special characters, drop the `\` to get back the original string value.
