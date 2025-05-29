```
SparseUnidimensionalInterpolator{T=eltype(ker)}(ker, d, pos, grd)
```

yields a linear mapping which interpolates the `d`-th dimension of an array with kernel `ker` at positions `pos` along the dimension of interpolation `d` and assuming the input array has grid coordinates `grd` along the the `d`-th dimension of interpolation.  Argument `pos` is a vector of positions, argument `grd` may be a range or the length of the dimension of interpolation.  Optional parameter `T` is the floating-point type of the coefficients of the operator.

This kind of interpolator is suitable for separable multi-dimensional interpolation with precomputed interpolation coefficients.  Having precomputed coefficients is mostly interesting when the operator is to be applied multiple times (for instance in iterative methods).  Otherwise, separable operators which compute the coefficients *on the fly* may be preferable.

A combination of instances of `SparseUnidimensionalInterpolator` can be built to achieve sperable multi-dimensional interpolation.  For example:

```
using LinearInterpolators
ker = CatmullRomSpline()
n1, n2 = 70, 50
x1 = linspace(1, 70, 201)
x2 = linspace(1, 50, 201)
A1 = SparseUnidimensionalInterpolator(ker, 1, x1, 1:n1)
A2 = SparseUnidimensionalInterpolator(ker, 2, x2, 1:n2)
A = A1*A2
```
