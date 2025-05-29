```
gensurf(fis::AbstractFuzzySystem; Npoints=100)
```

Plots the generating surface of the given fuzzy inference system. The given FIS must have exactly one output and at most two inputs.

### Inputs

  * `fis::AbstractFuzzySystem` – fuzzy inference system to plot
  * `Npoints::Int64 (default 100)` – number of sample points used for each input to plot the generating surface.
