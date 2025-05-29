```
StatsBase.confint(method::AMARI,
                  target::Empirikos.EBayesTarget,
                  Zs;
                  level=0.95)
```

Form a confidence interval for the [`Empirikos.EBayesTarget`](@ref) `target` with coverage     `level` based on the samples `Zs` using the [`AMARI`](@ref) `method`.
