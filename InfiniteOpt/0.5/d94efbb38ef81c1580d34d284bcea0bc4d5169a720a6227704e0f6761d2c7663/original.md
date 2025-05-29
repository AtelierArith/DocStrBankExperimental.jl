```
add_semi_infinite_variable(model::JuMP.Model, var::SemiInfiniteVariable, 
                           key::Val{:ext_key_name})::GeneralVariableRef
```

Add a semi-infinite variable `var` to the optimizer model `model` (with `key`)  and return the correct `InfiniteOpt` variable reference. This is an internal  method used by [`make_semi_infinite_variable_ref`](@ref) to make semi-infinite  variables when the `write_model` is an optimizer model. This is useful for  extensions that wish to expand measures, but without changing the original  `InfiniteModel`. An error is thrown for optimizer model types. Note if this is  extended, than [`internal_semi_infinite_variable`](@ref) should also be extended  in order to direct semi-infinite variables references to the underlying  [`SemiInfiniteVariable`](@ref).
