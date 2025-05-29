```
make_semi_infinite_variable_ref(write_model::Union{InfiniteModel, JuMP.Model},
                                ivref::GeneralVariableRef,
                                indices::Vector{Int},
                                values::Vector{Float64}
                                )::GeneralVariableRef
```

Make a semi-infinite variable for infinite variable/derivative/parameter  function `ivref` at `support`, add it to the `write_model`, and return the  `GeneralVariableRef`. This is an internal method for semi-infinite variables  produced by expanding measures via [`expand_measure`](@ref). This is also useful  for those writing extension optimizer models and wish to expand measures without  modifiying the `InfiniteModel`. In such cases, `write_model` should be the  optimizer model and  [`add_semi_infinite_variable`](@ref add_semi_infinite_variable(::JuMP.Model, ::Any, ::Any))  should be extended appropriately for semi-infinite variables. Errors if  `write_model` is an optimizer model and `add_semi_infinite_variable` is not  properly extended. Note this is only intended for optimizer models that are  currently stored in `InfiniteModel.optimizer_model`.
