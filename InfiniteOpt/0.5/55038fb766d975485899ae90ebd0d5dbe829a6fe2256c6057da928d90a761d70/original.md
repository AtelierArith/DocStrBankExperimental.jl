```
optimizer_model_expression(expr, key::Val{ext_key_name}; [kwargs...])
```

Return the reformulation expression(s) stored in the optimizer model that correspond to `expr`. This needs to be defined for extensions that implement a custom optimizer model type. Principally, this is accomplished by typed the `key` argument to `Val{ext_key_name}`. Keyword arguments can be added as needed. Note that if `expr` is a `GeneralVariableRef` this just dispatches to `optimizer_model_variable`.
