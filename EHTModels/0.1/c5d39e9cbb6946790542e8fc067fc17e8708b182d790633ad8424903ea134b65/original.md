```
RectangleFilter(θmaj, [θmin, ϕ]; [θunit, ϕunit])
```

Create an rectangle filter with the total flux density of unity.

Args:

  * `θmaj::Real`:   The major-axis size of the rectangle.
  * `θmin::Real`:   The minor-axis size of the rectangle. If `θmin < 0`, then   `θmin = θmax` (i.e. square). Default to -1.
  * `ϕ::Real`:   The position angle of the rectangle. Default to 0.
  * `θunit, ϕunit::Unitful`:   The unit for `θmaj` & `θmin` and `ϕ`, respectively.    Default: `θunit=rad` and `ϕ=deg`.
