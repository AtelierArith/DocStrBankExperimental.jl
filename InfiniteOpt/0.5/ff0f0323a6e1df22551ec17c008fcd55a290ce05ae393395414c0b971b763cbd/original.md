```
expression_supports(optimizer_model::JuMP.Model, expr,
                    key::Val{ext_key_name}; [kwargs...])
```

Return the supports associated with the mappings of `expr` in `optimizer_model`. This dispatches off of `key` which permits optimizer model extensions. This should throw an error if `expr` is not associated with the variable mappings stored in `optimizer_model`. Keyword arguments can be added as needed. Note that if `expr` is a `GeneralVariableRef` this just dispatches to `variable_supports`.
