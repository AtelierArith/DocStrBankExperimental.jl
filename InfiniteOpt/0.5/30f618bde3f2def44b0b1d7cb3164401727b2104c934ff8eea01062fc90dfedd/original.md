```
supports(pref::DependentParameterRef; 
         [label::Type{<:AbstractSupportLabel} = PublicLabel])::Vector{Float64}
```

Return the support points associated with `pref`. A subset of supports can be returned via `label` to return just the supports associated with `label`. By  default only the public supports are given, but the full set is  obtained via `label == All`.

**Example**

```julia-repl
julia> supports(x[1])
2-element Array{Float64,1}:
 0.0
 1.0
```
