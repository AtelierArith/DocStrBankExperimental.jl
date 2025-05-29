```
WS(stochasticprogram::TwoStageStochasticProgram, scenario::AbstractScenarioaData; optimizer = nothing)
```

Generate a **wait-and-see** (`WS`) model of the two-stage `stochasticprogram`, corresponding to `scenario`.

In other words, generate the first stage and the second stage of the `stochasticprogram` as if `scenario` is known to occur. Optionally, a capable `optimizer` can be supplied to `WS`.

See also: [`DEP`](@ref), [`EVP`](@ref)
