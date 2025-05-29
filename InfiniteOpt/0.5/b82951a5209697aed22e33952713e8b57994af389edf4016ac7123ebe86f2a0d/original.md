```
map_dual(cref::InfOptConstraintRef, key::Val{ext_key_name}, result::Int; 
         kwargs...)
```

Map the dual(s) of `cref` to its counterpart in the optimizer model type that is distininguished by its extension key `key` as type `Val{ext_key_name}`. Here `ref` need refer to methods for both variable references and constraint references. This only needs to be defined for reformulation extensions that cannot readily extend `optimizer_model_variable` and `optimizer_model_constraint`. Such as is the case with reformuations that do not have a direct mapping between variables and/or constraints in the original infinite form. Otherwise, `optimizer_model_variable` and `optimizer_model_constraint` are used to make these mappings by default where `kwargs` are also pass on to. Here `result` is  the result index that is used in `dual`. 
