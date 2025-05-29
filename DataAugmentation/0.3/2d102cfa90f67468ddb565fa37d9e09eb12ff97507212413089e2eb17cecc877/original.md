```
MaskMulti(a, [classes]; interpolate=BSpline(Constant()), extrapolate=Flat())
```

An `N`-dimensional multilabel mask with labels `classes`. Optionally, the interpolation and extrapolation method can be provided. Interpolation here refers to how the values of projected pixels that fall into the transformed content bounds are calculated. Extrapolation refers to how to assign values that fall outside the projected content bounds. The default is nearest neighbor interpolation and flat extrapolation of the edges into new regions.

!!! info
    The `Interpolations` package provides numerous methods for use with the `interpolate` and `extrapolate` keyword arguments.  For instance, `BSpline(Linear())` and `BSpline(Constant())` provide linear and nearest neighbor interpolation, respectively. In addition `Flat()`, `Reflect()` and `Periodic()` boundary conditions are available for extrapolation.


## Examples

```julia
using DataAugmentation

mask = MaskMulti(rand(1:3, 100, 100))
```

```julia
showitems(mask)
```
