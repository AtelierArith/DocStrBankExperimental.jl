```
AvgCutPruningAlgo <: AbstractCutPruningAlgo
```

Removes the cuts with lower trust where the trust is: nused / nwith + bonus where the cut has been used `nused` times amoung `nwith` optimization done with it. We say that the cut was used if its dual value is nonzero. It has a bonus equal to `mycutbonus` if the cut was generated using a trial given by the problem using this cut. If `nwidth` is zero, `nused/nwith` is replaced by `newcuttrust`.
