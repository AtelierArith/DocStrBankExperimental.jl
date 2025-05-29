```
make_point_variable_ref(write_model::Union{InfiniteModel, JuMP.Model},
                        ivref::GeneralVariableRef,
                        support::Vector{Float64}
                        )::GeneralVariableRef
```

Make a point variable for infinite variable/derivative `ivref` at `support`, add it to the `write_model`, and return the `GeneralVariableRef`. This is an internal method for point variables produced by expanding measures via [`expand_measure`](@ref). This is also useful for those writing extension optimizer models and wish to expand measures without modifiying the `InfiniteModel`. In such cases, `write_model` should be the optimizer model and  [`add_point_variable`](@ref add_point_variable(::JuMP.Model, ::Any, ::Any, ::Any))  should be extended appropriately for point variables. Errors if `write_model` is an optimizer model and `add_point_variable` is not properly extended. 

Note this is also accomodates infinite parameter functions, in which case the  infinite parameter function is called with the support as input. 
