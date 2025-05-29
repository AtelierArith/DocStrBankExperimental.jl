```
num_supports(pref::IndependentParameterRef; 
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

Return the number of support points associated with `pref`. By default, only the  number of public supports are counted. The full amount can be determined by setting  `label = All`. Moreover, the amount of labels that satisfy `label` is obtained  using an [`AbstractSupportLabel`](@ref).

**Example**

```julia-repl
julia> num_supports(t)
2
```
