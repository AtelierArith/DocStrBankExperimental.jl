```
function E4ST.modify_model!(pol::PTC, config, data, model)
```

Subtracts the PTC price * generation in that year from the objective function using [`add_obj_term!(data, model, PerMWhGen(), pol.name, oper = -)`](@ref)
