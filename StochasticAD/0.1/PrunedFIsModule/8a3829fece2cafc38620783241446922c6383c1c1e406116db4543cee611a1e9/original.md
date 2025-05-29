```
PrunedFIsBackend <: StochasticAD.AbstractFIsBackend
```

A backend algorithm that prunes between perturbations as soon as they clash (e.g. added together). Currently chooses uniformly between all perturbations.
