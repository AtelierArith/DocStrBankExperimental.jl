```
variable_supports(optimizer_model::JuMP.Model, vref,
                  key::Val{ext_key_name}; 
                  [kwargs...])::Vector
```

Return the supports associated with the mappings of `vref` in `optimizer_model`. This dispatches off of `key` which permits optimizer model extensions. This should throw an error if `vref` is not associated with the variable mappings stored in `optimizer_model`. Keyword arguments can be added as needed. Note that no extension is necessary for point or finite variables. 
