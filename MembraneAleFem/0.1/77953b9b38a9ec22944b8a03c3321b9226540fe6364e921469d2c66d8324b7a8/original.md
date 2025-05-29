```
GaussPointsζ(gpsξ::GaussPointsξ, ζlo::Float64, ζhi::Float64)
```

Weights $w_k$ and points $ζ_k$ with which a 1-D integral is approximated over `ζlo` ≤ `ζ` ≤ `ζhi`.

Calculated via the transform from `ξ` to `ζ` via the relations

`ζ`$_k$ = `ξ`$_k$ (`ζhi` - `ζlo`) / 2 + (`ζhi` + `ζlo`) / 2

$w_k$ = $\hat{w}_k$ (`ζhi` - `ζlo`) / 2

The struct has three fields:

  * `ngp` –> number of Gaussian quadrature points
  * `ζs`  –> set of points $ζ_k$
  * `ws`  –> set of weights $w_k$
