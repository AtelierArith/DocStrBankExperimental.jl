```
transf(object::Union{Pcr, Spcr}, X; nlv = nothing)
```

Compute latent variables (LVs = scores) from a fitted model and a matrix X.

  * `object` : The fitted model.
  * `X` : Matrix (m, p) for which LVs are computed.
  * `nlv` : Nb. LVs to consider.
