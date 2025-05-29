```
function E4ST.modify_model!(pol::ITCStorage, config, data, model)
```

Subtracts the ITCStorage price * Capacity in that year from the objective function using [`add_obj_term!(data, model, PerMWCap(), pol.name, oper = -)`](@ref)
