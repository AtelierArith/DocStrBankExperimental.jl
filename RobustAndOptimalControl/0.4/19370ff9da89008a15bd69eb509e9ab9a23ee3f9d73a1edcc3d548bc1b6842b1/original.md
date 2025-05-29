```
nu_reduction(G, g=0.1; gap = nugap(G))
```

Reduce the number of particles in an uncertain system `G` by removing all particles that are within the νgap `g` of the nominal system `Gₙ`.

Note: If `G` has a stochastic interpretation, i.e., the coefficients come from some distribution, this interpretation will be lost after reduction, mean values and standard deviations will not be preserved. The reduced system should instead be interpreted as preserving worst-case uncertainty.

If the `gap = nugap(G)` has already been precomputed, it can be supplied as an argument to avoid potentially costly recomputation.
