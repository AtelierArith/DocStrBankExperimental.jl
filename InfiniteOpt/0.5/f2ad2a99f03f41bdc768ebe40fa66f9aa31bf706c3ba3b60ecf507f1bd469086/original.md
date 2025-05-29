```
JuMP.lp_sensitivity_report(model::InfiniteModel; 
                           [atol::Float64 = 1e-8])::InfOptSensitivityReport
```

Extends `JuMP.lp_sensitivity_report` to generate and return an LP sensitivity  report in accordance with the optimizer model. See  [`InfOptSensitivityReport`](@ref) for syntax details on how to query it. `atol`  denotes the optimality tolerance and should match that used by the solver to  compute the basis. Please refer to `JuMP`'s documentation for more technical  information on interpretting the output of the report.

**Example**

```julia-repl
julia> report = lp_sensitivity_report(model);

julia> report[x]
(0.0, 0.5)
```
