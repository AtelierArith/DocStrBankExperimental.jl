```
interpolate(x, y, BSplineOrder(k), [bc = nothing])
```

Interpolate values `y` at locations `x` using B-splines of order `k`.

Grid points `x` must be real-valued and are assumed to be in increasing order.

Returns a [`SplineInterpolation`](@ref) which can be evaluated at any intermediate point.

Optionally, one may pass one of the boundary conditions listed in the [Boundary conditions](@ref boundary-conditions-api) section. Currently, the [`Natural`](@ref) and [`Periodic`](@ref) boundary conditions are available.

See also [`interpolate!`](@ref).

!!! note "Periodic boundary conditions"
    Periodic boundary conditions should be used if the interpolated data is supposed to represent a periodic signal. In this case, pass `bc = Period(L)`, where `L` is the period of the x-axis. Note that the endpoint `x[begin] + L` should *not* be included in the `x` vector.


!!! note "Cubic periodic splines"
    *Cubic* periodic splines (`BSplineOrder(4)`) are particularly well optimised compared to periodic splines of other orders. Just note that interpolations using cubic periodic splines modify their input (including `x` and `y` values).


# Examples

```jldoctest interpolate
julia> xs = -1:0.1:1;

julia> ys = cospi.(xs);

julia> S = interpolate(xs, ys, BSplineOrder(4))
SplineInterpolation containing the 21-element Spline{Float64}:
 basis: 21-element BSplineBasis of order 4, domain [-1.0, 1.0]
 order: 4
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.7, -0.6, -0.5, -0.4, -0.3  …  0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 1.0, 1.0, 1.0, 1.0]
 coefficients: [-1.0, -1.00111, -0.8975, -0.597515, -0.314147, 1.3265e-6, 0.314142, 0.597534, 0.822435, 0.96683  …  0.96683, 0.822435, 0.597534, 0.314142, 1.3265e-6, -0.314147, -0.597515, -0.8975, -1.00111, -1.0]
 interpolation points: -1.0:0.1:1.0

julia> S(-1)
-1.0

julia> (Derivative(1) * S)(-1)
-0.01663433622896893

julia> (Derivative(2) * S)(-1)
10.527273287554928

julia> Snat = interpolate(xs, ys, BSplineOrder(4), Natural())
SplineInterpolation containing the 21-element Spline{Float64}:
 basis: 21-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0], BCs {left => (D{2},), right => (D{2},)}
 order: 4
 knots: [-1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4  …  0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0]
 coefficients: [-0.833333, -0.647516, -0.821244, -0.597853, -0.314057, -2.29076e-5, 0.314148, 0.597532, 0.822435, 0.96683  …  0.96683, 0.822435, 0.597532, 0.314148, -2.29076e-5, -0.314057, -0.597853, -0.821244, -0.647516, -0.833333]
 interpolation points: -1.0:0.1:1.0

julia> Snat(-1)
-1.0

julia> (Derivative(1) * Snat)(-1)
0.2872618670889516

julia> (Derivative(2) * Snat)(-1)
-3.33066907387547e-14

```

## Periodic boundary conditions

Interpolate $f(x) = \cos(πx)$ for $x ∈ [-1, 1)$. Note that the period is $L = 2$ and that the endpoint ($x = 1$) must *not* be included in the data points.

```jldoctest interpolate
julia> xp = -1:0.1:0.9;

julia> yp = cospi.(xp);

julia> Sper = interpolate(xp, yp, BSplineOrder(4), Periodic(2))
SplineInterpolation containing the 20-element Spline{Float64}:
 basis: 20-element PeriodicBSplineBasis of order 4, domain [-1.0, 1.0), period 2.0
 order: 4
 knots: [..., -1.2, -1.1, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4, -0.3  …  0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.1, ...]
 coefficients: [..., -1.01659, -0.96683, -0.822435, -0.597534, -0.314142, 1.10589e-17, 0.314142, 0.597534, 0.822435, 0.96683, 1.01659, 0.96683, 0.822435, 0.597534, 0.314142, 1.51788e-17, -0.314142, -0.597534, -0.822435, -0.96683, ...]
 interpolation points: -1.0:0.1:0.9
```

As expected, the periodic spline does a better job at approximating the periodic function $f(x) = \cos(πx)$ near the boundaries than the other interpolations:

```jldoctest interpolate
julia> x = -0.99; cospi(x), Sper(x), Snat(x), S(x)
(-0.9995065603657316, -0.9995032595823043, -0.9971071640321145, -0.9996420091470221)

julia> x = 0.998; cospi(x), Sper(x), Snat(x), S(x)
(-0.9999802608561371, -0.9999801044078943, -0.9994253145274461, -1.0000122303614758)
```
