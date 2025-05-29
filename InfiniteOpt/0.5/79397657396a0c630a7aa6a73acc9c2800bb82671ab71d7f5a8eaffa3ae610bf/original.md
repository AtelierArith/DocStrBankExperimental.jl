```
optimizer_model_variable(vref::GeneralVariableRef, key::Val{ext_key_name};
                         [kwargs...])
```

Return the reformulation variable(s) stored in the optimizer model that correspond to `vref`. This needs to be defined for extensions that implement a custom optimizer model type. Principally, this is accomplished by typed the `key` argument to `Val{ext_key_name}`. Keyword arguments can be added as needed.
