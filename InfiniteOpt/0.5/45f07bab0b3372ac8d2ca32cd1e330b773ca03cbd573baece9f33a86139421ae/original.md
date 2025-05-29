```
has_supports(prefs::AbstractArray{<:DependentParameterRef})::Bool
```

Return true if `prefs` have supports or false otherwise. Errors if not all of the infinite dependent parameters are from the same object.

**Example**

```julia-repl
julia> has_supports(x)
true
```
