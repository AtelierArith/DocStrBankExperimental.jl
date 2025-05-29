```
pool(mira::Mira)
```

Pools the results of multiply imputed repeated analyses (`Mira`). The function will work on any `Mira` object containing model outputs which are receptive to the `coef`, `stderror` and `nobs` functions from StatsAPI.jl.
