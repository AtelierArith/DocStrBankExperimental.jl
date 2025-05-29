```
set_supports(
    prefs::Union{Vector{GeneralVariableRef}, AbstractArray{<:GeneralVariableRef}},
    supports::Union{Array{<:Real, 2}, Vector{<:AbstractArray{<:Real}}};
    [force::Bool = false]
    )::Nothing
```

Set the support points associated with dependent infinite parameters `prefs`. An `ArgumentError` is thrown if `prefs` is are not dependent infinite parameters.
