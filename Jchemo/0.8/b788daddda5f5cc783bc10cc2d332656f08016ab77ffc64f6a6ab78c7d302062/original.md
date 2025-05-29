```
predict(object::Kplsr, X; nlv = nothing)
```

Compute Y-predictions from a fitted model.

  * `object` : The fitted model.
  * `X` : X-data for which predictions are computed.
  * `nlv` : Nb. LVs, or collection of nb. LVs, to consider.

If nothing, it is the maximum nb. LVs.
