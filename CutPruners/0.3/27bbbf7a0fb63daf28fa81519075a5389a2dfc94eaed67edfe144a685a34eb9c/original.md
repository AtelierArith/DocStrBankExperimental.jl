```
DecayCutPruningAlgo <: AbstractCutPruningAlgo
```

Removes the cuts with lower trust where the trust is initially `newcuttrust + bonus` and is updated using `trust -> λ * trust + used` after each optimization done with it. The value `used` is 1 if the cut was used and 0 otherwise. It has a bonus equal to `mycutbonus` if the cut was generated using a trial given by the problem using this cut. We say that the cut was used if its dual value is nonzero.
