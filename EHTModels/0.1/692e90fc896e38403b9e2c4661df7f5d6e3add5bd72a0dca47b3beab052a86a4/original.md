```
CircularGaussian(F, θmaj, [x0, y0]; [θunit, ϕunit])
```

Create an circular Gaussian.

Args:

  * `F::Real`:   The total flux desnity of the Gaussian.
  * `θfwhm::Real`:   The FWHM size of the Gaussian.
  * `x0, y0::Real`:   The centoral position in the unit of θunit. Default to 0.
  * `θunit::Unitful`:   The unit for `θ`, `x0` and `y0`, respectively.    Default: `θunit=rad`.
