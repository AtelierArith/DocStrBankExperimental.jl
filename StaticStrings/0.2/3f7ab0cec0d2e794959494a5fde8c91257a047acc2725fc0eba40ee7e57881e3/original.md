```
substatic"string"[N]
```

Create a [`SubStaticString`](@ref) from "string". Optionally, specify the number of codeunits, `N`. The result will be a `SubStaticString{N}` but the codeunits used will be those of the original string.

# Examples

```jldoctest
julia> substatic"Як ти?"
substatic"Як ти?"10

julia> substatic"Як ти?"256
substatic"Як ти?"256
```
