```
EllipticalGaussian(F, θmaj, [θmin, ϕ, x0, y0]; [θunit, ϕunit])
```

Create an elliptical Gaussian.

Args:

  * `F::Real`:   The total flux desnity of the Gaussian.
  * `θmaj::Real`:   The major-axis FWHM size of the Gaussian.
  * `θmin::Real`:   The minor-axis FWHM size of the Gaussian. If `θmin < 0`, then   `θmin = θmax` (i.e. circular Gaussian). Default to -1.
  * `ϕ::Real`:   The position angle of the Gausian. Default to 0.
  * `x0, y0::Real`:   The centoral position in the unit of θunit. Default to 0.
  * `θunit::Unitful`:   The unit for `θmaj`, `θmin`, `x0` and `y0`. Default: `θunit=rad`.
  * `ϕunit::Unitful`:   The unit for `ϕ`. Default: `ϕ=deg`.
