```
get_variables(T::Type, [order::Int=get_order()])
```

Return a `TaylorN{T}` vector with each entry representing an independent variable. It takes the default `_params_TaylorN_` values if `set_variables` hasn't been changed with the exception that `order` can be explicitly established by the user without changing internal values for `num_vars` or `variable_names`. Omitting `T` defaults to `Float64`.
