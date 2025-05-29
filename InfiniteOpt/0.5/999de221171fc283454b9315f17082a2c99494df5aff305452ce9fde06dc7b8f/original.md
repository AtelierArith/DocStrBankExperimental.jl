```
add_supports(
    prefs::Union{Vector{GeneralVariableRef}, AbstractArray{<:GeneralVariableRef}},
    supports::Union{Array{<:Real, 2}, Vector{<:AbstractArray{<:Real}}}
    )::Nothing
```

Add the support points `supports` to the dependent infinite parameters `prefs`. An `ArgumentError` is thrown if `prefs` is are not dependent infinite parameters.
