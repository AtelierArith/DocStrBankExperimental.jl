```
make_reduced_expr(vref::GeneralVariableRef, pref::GeneralVariableRef, 
                  support::Float64, write_model::Union{InfiniteModel, JuMP.Model})
```

Given the argument variable `vref` and the operator parameter `pref` from a  derivative, build and return the reduced expression in accordance to the support  `support` with respect to `pref`. New point/semi-infinite variables will be written to  `write_model`. This is solely intended as a helper function for derivative  evaluation.
