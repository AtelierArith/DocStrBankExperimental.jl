```
Curve(x:: AbstractVector, y:: AbstractVector; method=ItpLinear(), extrapolation=EtpFlat(), logx=false, logy=false, sort=true)
```

Standard curve constructor. Creates the interpolation/extrapolation object of the curve instance. The points `x` and `y` do not need to be sorted, this is done in the Curve constructor.

Interpolation/extrapolation details can be changed using the keyword arguments, defaults are:

  * linear interpolation
  * constant extrapolation
  * no logarithmic axes

Note that for method ˋGridded(x)ˋ must be used so that the x-grid can be non-uniform.

Valid choices for ˋmethodˋ are:

  * ˋItpLinear()ˋ, corresponds to Interpolation.jl ˋGridded(Linear())ˋ - default
  * ˋItpConstant()ˋ, corresponds to Interpolation.jl ˋGridded(Constant())ˋ

Valid choices for ˋextrapolationˋ are:

  * ˋEtpFlat()ˋ, corresponds to Interpolation.jl ˋFlat()ˋ - default
  * ˋEtpLine()ˋ, corresponds to Interpolation.jl ˋLine()ˋ

If the curve consists only of a single point, always constant extrapolation is used.

  * `sort=true`: per default, the input points are sorted and duplicate x-values are removed. `sort=true` is unsafe and intended to be used for Curves.jl internal operations only, where it can be guaranteed that the points are sorted and not duplicate.
