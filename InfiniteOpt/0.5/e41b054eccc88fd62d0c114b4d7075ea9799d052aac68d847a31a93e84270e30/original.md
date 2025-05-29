```
num_supports(pref::DependentParameterRef; 
             [label::Type{<:AbstractSupportLabel} = PublicLabel])::Int
```

Return the number of support points associated with a single dependent infinite parameter `pref`. Specify a subset of supports via `label` to only count the supports with `label`. By default only the amount of public supports are given, but  the full amount is obtained via `label == All`.

**Example**

```julia-repl
julia> num_supports(x[1])
2

julia> num_supports(x[1], label = MCSample)
0
```
