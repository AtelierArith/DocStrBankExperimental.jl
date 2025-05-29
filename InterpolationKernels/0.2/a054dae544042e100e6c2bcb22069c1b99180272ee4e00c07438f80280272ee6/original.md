```
CubicSpline{T}(a, b) -> ker
```

yields an instance of a generic cubic spline for floating-point type `T` and parameters `a = ker'(1)` and `b = ker(1)` the slope and the value of the function `ker(x)` at `x = 1`.

A cubic spline kernel is at least C¹ continuous, the expression `ker'` yields a kernel instance implementing the 1st derivative of the generic cubic spline `ker` (see [`CubicSplinePrime`](@ref) to directly build a derivative).

Depending on the values of the parameters `a` and `b`, more specific cubic spline kernels can be emulated:

  * `CubicSpline{T}(-1/2,1/6)` yields a cubic B-spline as built by `BSpline{4,T}()`.
  * `CubicSpline{T}(a,0)` yields a cardinal cubic spline as built by `CardinalCubicSpline{T}(a)`.
  * `CubicSpline{T}(-1/2,0)` yields a Catmull-Rom kernel as built by `CatmullRomSpline{T}()`.
  * `CubicSpline{T}(-b/2-c,b/6)` yields Mitchell & Netravali cubic spline as built by `MitchellNetravaliSpline{T}(b,c)`.

Instances of `CubicSpline` are very well optimized and, in practice, they may be as fast or even faster than these more specialized counterparts.
