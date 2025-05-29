```
ParameterPlot(R::MultistartResults; st=:dotplot, BiLog::Bool=true, Nsteps::Int=5, StepTol::Real=1e-3, MaxValue=3000)
```

Plots the parameter values of the `MultistartResults` separated by step to show whether the different optima are localized or not. `st` can be either `:dotplot`, `:boxplot` or `:violin`.

!!! note
    StatsPlots.jl needs to be loaded to use this plotting function.

