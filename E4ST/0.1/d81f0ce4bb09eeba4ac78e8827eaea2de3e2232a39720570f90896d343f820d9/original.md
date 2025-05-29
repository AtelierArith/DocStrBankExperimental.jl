```
function E4ST.modify_model!(pol::ITC, config, data, model)
```

Subtracts the ITC price * Capacity in that year from the objective function using [`add_obj_term!(data, model, PerMWCap(), pol.name, oper = -)`](@ref)
