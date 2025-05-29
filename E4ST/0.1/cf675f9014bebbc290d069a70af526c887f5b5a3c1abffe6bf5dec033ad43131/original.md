```
E4ST.modify_model!(pol::EmissionPrice, config, data, model)
```

Adds a column to the gen table containing the emission price as a per MWh value (gen emission rate * emission price).  Adds this as a `PerMWhGen` price to the objective function using [`add_obj_term!`](@ref)
