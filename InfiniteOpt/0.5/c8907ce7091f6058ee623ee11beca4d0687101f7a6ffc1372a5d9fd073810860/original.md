```
constraint_supports(optimizer_model::JuMP.Model, 
                    cref::InfOptConstraintRef,
                    key::Val{ext_key_name}; [kwargs...])
```

Return the supports associated with the mappings of `cref` in `optimizer_model`. This dispatches off of `key` which permits optimizer model extensions. This should throw an error if `cref` is not associated with the variable mappings stored in `optimizer_model`. Keyword arguments can be added as needed.
