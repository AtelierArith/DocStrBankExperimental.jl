```
 ffm2psm(Af::FourierFunctionMatrix, nrange atol = 0, rtol = 10*n*ϵ,) -> A::Matrix{Num}
```

Convert a range of harmonic components `nrange` of the Fourier function matrix `Af` to a symbolic matrix `A`.  The default range is `nrange = 0:n`, where `n` is the order of the maximum harmonics.  The tolerance used to assess nonzero coefficients is `tol = max(atol, rtol*maxnorm)`, where  `maxnorm` is the maximum absolute value of the coefficients `ac_i` and `as_i` in `Af(t)`. The default values of tolerances are `atol = 0` and `rtol = 10*n*ϵ`, where `ϵ` is the working machine precision.
