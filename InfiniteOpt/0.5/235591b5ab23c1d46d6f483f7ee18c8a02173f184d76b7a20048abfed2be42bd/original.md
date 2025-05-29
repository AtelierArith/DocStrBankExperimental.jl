```
map_value([ref/expr], key::Val{ext_key_name}, result::Int; kwargs...)
```

Map the value(s) of `ref` to its counterpart in the optimizer model type that is distininguished by its extension key `key` as type `Val{ext_key_name}`. Here `ref` need refer to methods for both variable references and constraint references. This only needs to be defined for reformulation extensions that cannot readily extend `optimizer_model_variable`, `optimizer_model_expression`, and/or `optimizer_model_constraint`. Such as is the case with reformuations that do not have a direct mapping between variables and/or constraints in the original infinite form. Otherwise, `optimizer_model_variable`, `optimizer_model_expression`, and `optimizer_model_constraint` are used to make these mappings by default where `kwargs` are passed on these functions. Here  `result` is the result index used in `value`.
