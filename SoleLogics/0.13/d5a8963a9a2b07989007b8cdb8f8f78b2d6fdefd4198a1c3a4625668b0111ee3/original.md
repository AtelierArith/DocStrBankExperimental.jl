```
ismodal(::Type{<:Connective})::Bool = false
ismodal(c::Connective)::Bool = ismodal(typeof(c))
```

Return whether it is known that an `Connective` is modal.

# Examples

```julia-repl
julia> ismodal(◊)
true

julia> ismodal(∧)
false
```
