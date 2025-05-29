```
function resolve_units!(
    data::Dict{String,<:Any};
    multinetwork::Bool=false,
    number_multinetworks::Int=0
)
```

Resolve the units used throughout the disparate datasets by setting the same settings bases. `data` is the pmitd dictionary to be corrected by resolving units, `multinetwork` is the boolean that defines if there are multiple networks that need to be corrected, and `number_multinetworks` defines the number of multinetworks.
