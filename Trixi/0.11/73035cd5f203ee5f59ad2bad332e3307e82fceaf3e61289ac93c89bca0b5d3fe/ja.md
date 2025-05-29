```
VolumeIntegralFluxDifferencing(volume_flux)
```

DG法に基づく体積積分型で、SBP演算子と対称二点`volume_flux`を用いたフラックス差分を使用します。この`volume_flux`は、Trixi.jlにおける数値フラックスのインターフェースを満たす必要があります。

## 参考文献

  * LeFloch, Mercier, Rohde (2002) Fully Discrete, Entropy Conservative Schemes of Arbitrary Order [doi: 10.1137/S003614290240069X](https://doi.org/10.1137/S003614290240069X)
  * Fisher, Carpenter (2013) High-order entropy stable finite difference schemes for nonlinear conservation laws: Finite domains [doi: 10.1016/j.jcp.2013.06.014](https://doi.org/10.1016/j.jcp.2013.06.014)
  * Hendrik Ranocha (2017) Comparison of Some Entropy Conservative Numerical Fluxes for the Euler Equations [arXiv: 1701.02264](https://arxiv.org/abs/1701.02264) [doi: 10.1007/s10915-017-0618-1](https://doi.org/10.1007/s10915-017-0618-1)
  * Chen, Shu (2017) Entropy stable high order discontinuous Galerkin methods with suitable quadrature rules for hyperbolic conservation laws [doi: 10.1016/j.jcp.2017.05.025](https://doi.org/10.1016/j.jcp.2017.05.025)
