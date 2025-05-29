```
set_infinite_domain(prefs::AbstractArray{<:GeneralVariableRef},
                 domain::InfiniteArrayDomain)::Nothing
```

Specify the multi-dimensional infinite domain of the dependent infinite parameters `prefs` to `domain`. Note this will reset/delete all the supports contained in the underlying [`DependentParameters`](@ref) object. This will error if the not all of the dependent infinite parameters are included or if any of them are used by measures. An `ArgumentError` is thrown if `prefs` are not dependent infinite parameters.
