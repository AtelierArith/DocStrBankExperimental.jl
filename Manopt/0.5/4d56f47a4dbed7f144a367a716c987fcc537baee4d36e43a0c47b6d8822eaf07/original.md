```
update_storage!(a::AbstractStateAction, d::Dict{Symbol,<:Any})
```

Update the [`AbstractStateAction`](@ref) `a` internal values to the ones given in the dictionary `d`. The values are merged, where the values from `d` are preferred.
