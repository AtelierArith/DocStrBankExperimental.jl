```
pspole(psys::PeriodicStateSpace{PM}[,K]; kwargs...) -> val
```

Return for the periodic system `psys = (A(t),B(t),C(t),D(t))` the complex vector `val` containing  the characteristic exponents of the periodic matrix `A(t)` (also called the *poles* of the system `psys`). 

Depending on the underlying periodic matrix type `PM`, the optional argument `K` and keyword arguments `kwargs` may have the following values:

  * if `PM = PeriodicFunctionMatrix`, or `PM = PeriodicSymbolicMatrix`, or `PM = PeriodicTimeSeriesMatrix`, then `K` is the number of factors used to express the monodromy matrix of `A(t)` (default: `K = 1`)  and `kwargs` are the keyword arguments of  `PeriodicMatrices.pseig(::PeriodicFunctionMatrix)`;
  * if `PM = HarmonicArray`, then `K` is the number of harmonic components used to represent the Fourier series of `A(t)` (default: `K = max(10,nh-1)`, `nh` is the number of harmonics terms of `A(t)`)  and `kwargs` are the keyword arguments of  `PeriodicMatrices.psceig(::HarmonicArray)`;
  * if `PM = FourierFunctionMatrix`, then `K` is the number of harmonic components used to represent the Fourier series of `A(t)` (default: `K = max(10,nh-1)`, `nh` is the number of harmonics terms of `A(t)`)  and `kwargs` are the keyword arguments of  `PeriodicMatrices.psceig(::FourierFunctionMatrix)`;
  * if `PM = PeriodicMatrix` or `PM = PeriodicArray`, then `K` is the starting sample time (default: `K = 1`)  and `kwargs` are the keyword arguments of  `PeriodicMatrices.psceig(::PeriodicMatrix)`;
