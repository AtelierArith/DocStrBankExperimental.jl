```
transf(object::Comdim, Xbl; nlv = nothing)
transfbl(object::Comdim, Xbl; nlv = nothing)
```

Compute latent variables (LVs = scores) from a fitted model.

  * `object` : The fitted model.
  * `Xbl` : A list of blocks (vector of matrices)    of X-data for which LVs are computed.
  * `nlv` : Nb. LVs to compute.
