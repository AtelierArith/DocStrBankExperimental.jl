```
solve!(model::Model, analysistype::AbstractAnalysisType)::Model
```

Function used to perform (geometrically) linear and nonlinear and (materially) elastic and inelastic analyses.

!!! note
    This function is mutating and will update the state of the model.

