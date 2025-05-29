```
GaussianFilter(θmaj, [θmin, ϕ]; [θunit, ϕunit])
```

Create an elliptical Gaussian filter with the total flux density of unity centered at the origin.

Args:

  * `θmaj::Real`:   The major-axis FWHM size of the Gaussian.
  * `θmin::Real`:   The minor-axis FWHM size of the Gaussian. If `θmin < 0`, then   `θmin = θmax` (i.e. circular Gaussian). Default to -1.
  * `ϕ::Real`:   The position angle of the Gausian. Default to 0.
  * `θunit, ϕunit::Unitful`:   The unit for `θmaj` & `θmin` and `ϕ`, respectively.    Default: `θunit=rad` and `ϕ=deg`.
