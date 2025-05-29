```
function apply_kron_reduction!(
    pmitd_data::Dict{String,<:Any}
)
```

Applies the corresponding transformation that applies a Kron Reduction to the network, reducing out the `kr_neutral`, leaving only the `kr_phases`.
