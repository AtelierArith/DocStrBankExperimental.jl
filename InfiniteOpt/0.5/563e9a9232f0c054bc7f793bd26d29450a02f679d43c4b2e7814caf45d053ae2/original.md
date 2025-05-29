```
supports(prefs::AbstractArray{<:DependentParameterRef};
         [label::Type{<:AbstractSupportLabel} = PublicLabel]
         )::Union{Vector{<:AbstractArray{<:Real}}, Array{Float64, 2}}
```

Return the support points associated with `prefs`. Errors if not all of the infinite dependent parameters are from the same object. This will return a matrix if `prefs` is `Vector`, otherwise a vector of arrays is returned where each  array is a support point matching the format of `prefs`. A subset of supports can be returned via `label` to return just the supports associated with `label`. By  default only the public supports are given, but the full set is  obtained via  `label == All`.

**Example**

```julia-repl
julia> supports(x) # columns are supports
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
```
