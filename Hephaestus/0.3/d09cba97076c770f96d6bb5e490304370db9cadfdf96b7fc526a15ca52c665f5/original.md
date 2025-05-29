```
solve(model::Model, analysistype::AbstractAnalysisType)::AbstractSolutionCache
```

Function used to perform elastic buckling and free vibration analyses.

!!! note
    This function is nonmutating and will not update the state of the model. Instead, it return a solution cache object that can be used to extract the results.

