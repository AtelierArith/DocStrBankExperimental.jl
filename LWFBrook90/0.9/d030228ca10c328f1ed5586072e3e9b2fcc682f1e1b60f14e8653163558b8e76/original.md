```
plotamounts(simulation::DiscretizedSPAC)
plotamounts(simulation::DiscretizedSPAC, compartments::Symbol)
plotamounts(simulation::DiscretizedSPAC, compartments::Symbol, RWUcentroid::Symbol)
```

Plots the amount results of a SPAC Simulation. By default both above and belowground. The user can override this with the second argument isotope as one of `:aboveground`, `:belowground`, or `:above_and_belowground`. RWUcentroid can have values of either `:dontShowRWUcentroid` or `:showRWUcentroid`.
