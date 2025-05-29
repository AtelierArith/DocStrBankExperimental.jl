```
function make_lossless!(
    pmitd_data::Dict{String,<:Any}
)
```

Applies the corresponding transformation that removes parameters from objects with loss models to make them lossless. This includes switches voltage sources and transformers, which all have loss model parameters that can be omitted.
