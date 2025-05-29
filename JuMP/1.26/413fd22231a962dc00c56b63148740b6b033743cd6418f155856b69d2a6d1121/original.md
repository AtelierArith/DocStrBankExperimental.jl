```
reverse_sense(::Val{T}) where {T}
```

Given an (in)equality symbol `T`, return a new `Val` object with the opposite (in)equality symbol.

This function is intended for use in JuMP extensions.

## Example

```jldoctest
julia> reverse_sense(Val(:>=))
Val{:<=}()
```
