```
function remove_all_bounds!(
    pmitd_data::Dict{String,<:Any};
    exclude::Vector{<:String}=String["energy_ub"]
)
```

Applies the corresponding transformation that removes all fields ending in '*ub' or '*lb' that aren't required by the math model. Properties can be excluded from this removal with `exclude::Vector{String}`. By default, `"energy_ub"` is excluded from this removal, since it is a required property on storage (in pmd).
