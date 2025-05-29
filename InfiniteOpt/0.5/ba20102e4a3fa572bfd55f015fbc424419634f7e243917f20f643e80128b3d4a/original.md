```
map_reduced_cost(vref::GeneralVariableRef, key::Val{ext_key_name}, 
                  result::Int; kwargs...)
```

Map the reduced cost(s) of `vref` to its counterpart in the optimizer model type that is distininguished by its extension key `key` as type `Val{ext_key_name}`. This only needs to be defined for reformulation extensions that cannot readily extend `optimizer_model_variable`. Such as is the case with reformulations  that do not have a direct mapping between variables in the original infinite form. Otherwise, `optimizer_model_variable`, is used to make these mappings by default where `kwargs` are passed on these functions. Here  `result` is the result index used in `value`.
