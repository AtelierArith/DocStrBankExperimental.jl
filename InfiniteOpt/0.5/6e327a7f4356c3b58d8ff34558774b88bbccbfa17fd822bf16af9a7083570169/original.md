```
num_supports(prefs::AbstractArray{<:DependentParameterRef};
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

Return the number of support points associated with dependent infinite parameters `prefs`. Errors if not all from the same underlying object. Specify a subset of supports via `label` to only count the supports with `label`. By default only the amount of public supports are given, but the full amount is  obtained via `label == All`.

**Example**

```julia-repl
julia> num_supports(x)
2
```
