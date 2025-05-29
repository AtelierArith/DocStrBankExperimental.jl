```
AnalysisCallbackCoupled(semi, callbacks...)
```

Combine multiple analysis callbacks for coupled simulations with a [`SemidiscretizationCoupled`](@ref). For each coupled system, an indididual [`AnalysisCallback`](@ref) **must** be created and passed to the `AnalysisCallbackCoupled` **in order**, i.e., in the same sequence as the indidvidual semidiscretizations are stored in the `SemidiscretizationCoupled`.

!!! warning "Experimental code"
    This is an experimental feature and can change any time.

