```
DEP(stochasticprogram::TwoStageStochasticProgram; optimizer = nothing)
```

Generate the **deterministically equivalent problem** (`DEP`) of the two-stage `stochasticprogram`, unless a cached version already exists.

In other words, generate the extended form the `stochasticprogram` as a single JuMP model. Optionally, a capable `optimizer` can be supplied to `DEP`.

See also: [`VRP`](@ref), [`WS`](@ref)
