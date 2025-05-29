```
MitchellNetravaliSpline{T}(b=1/3, c=1/3)
```

yields an instance of the Mitchell & Netravali family of kernels for floating-point type `T` and parameters `(b,c)`.

These kernels are cubic splines which depends on 2 parameters, `b` and `c`. Whatever the values of `(b,c)`, Mitchell & Netravali kernels are normalized, even and C¹ continuous functions (these kernels and their first derivatives are continuous).

Taking `b = 0` yields the family of cardinal cubic splines (see [`CardinalCubicSpline`](@ref)) and is a sufficient and necessary condition to have Mitchell & Netravali kernels be cardinal functions.

Using the constraint: `b + 2c = 1` yields a cubic filter with, at least, quadratic order approximation.

Some specific values of `(b,c)` yield other well known kernels:

```
(b,c) = (1,0)      --> cubic B-spline
(b,c) = (0,-a)     --> Keys's cardinal cubic spline CardinalCubicSpline(a)
(b,c) = (0,1/2)    --> Catmull-Rom kernel CatmullRomSpline()
(b,c) = (b,0)      --> Duff's tensioned B-spline
(b,c) = (6β,-α-3β) --> generic cubic spline CubicSpline(α,β)
(b,c) = (1/3,1/3)  --> recommended by Mitchell-Netravali
```

The expression `ker'` yields a kernel instance which is the 1st derivative of the Mitchell & Netravali kernel `ker` (also see the constructor [`MitchellNetravaliSplinePrime`](@ref)).

Mitchell & Netravali family of kernels are currently instances of [`CubicSpline`](@ref).

Reference:

  * [Mitchell & Netravali, "*Reconstruction Filters in Computer Graphics*", in Computer Graphics, Vol. 22, Num. 4 (1988)](http://www.cs.utexas.edu/users/fussell/courses/cs384g/lectures/mitchell/Mitchell.pdf).
