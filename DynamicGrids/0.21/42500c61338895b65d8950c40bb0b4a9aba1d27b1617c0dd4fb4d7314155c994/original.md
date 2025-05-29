```
SparseOpt <: PerformanceOpt

SparseOpt()
```

An optimisation flag that ignores all padding valuesin the grid, by default zeros.

For low-density simulations performance may improve by orders of magnitude, as only used cells are run.

Specifiy with:

```julia
ruleset = Ruleset(rule; opt=SparseOpt())
# or
output = sim!(output, rule; opt=SparseOpt())
```

`SparseOpt` is best demonstrated with this simulation, where the grey areas do not run except where the neighborhood partially hangs over an area that is not grey:

![SparseOpt demonstration](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/complexlife_spareseopt.gif)
