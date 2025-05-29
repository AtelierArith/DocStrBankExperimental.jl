```
add_point_variable(model::JuMP.Model, ivref::GeneralVariableRef, 
                   support::Vector{Float64}, key::Val{:ext_key_name}
                   )::GeneralVariableRef
```

Add a point variable (defined by restricting `ivref` to `support`) to the  optimizer model `model` (with `key`) and return the correct `InfiniteOpt`  variable reference. This is an internal method used by  [`make_point_variable_ref`](@ref) to make point variables when the `write_model`  is an optimizer model. This is useful for extensions that wish to expand  measures, but without changing the original `InfiniteModel`. An error is thrown  for unextended optimizer model types.
