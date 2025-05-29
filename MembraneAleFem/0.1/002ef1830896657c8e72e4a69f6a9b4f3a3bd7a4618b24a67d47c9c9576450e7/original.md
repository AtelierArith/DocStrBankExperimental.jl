```
GaussPointsξ(ngp::Int64)
```

Weights $\hat{w}_k$ and points $ξ_k$ on the interval $[-1, +1]$ with which a 1-D integral is approximated.

The struct has three fields:

  * `ngp` –> number of Gaussian quadrature points
  * `ξs`  –> set of points $ξ_k$
  * `ws`  –> set of weights $\hat{w}_k$

Calculations from [Wikipedia: Gaussian quadrature](https://en.wikipedia.org/wiki/Gaussian_quadrature#Gauss.E2.80.93Legendre_quadrature).
