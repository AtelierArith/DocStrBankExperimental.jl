```
fit(BSplineOrder(4), xs, ys, λ::Real, [bc = Natural()]; [weights = nothing])
```

Fit a cubic smoothing spline to the given data.

Returns a cubic spline which roughly passes through the data (points `(xs[i], ys[i])`) given some smoothing parameter $λ$. Note that $λ = 0$ means no smoothing and the results are equivalent to all the data.

One can optionally pass a `weights` vector if one desires to give different weights to different data points (e.g. if one wants the curve to pass as close as possible to a specific point). By default all weights are $w_i = 1$.

More precisely, the returned spline $S(x)$ minimises:

$$
∑_{i = 1}^N w_i |y_i - S(x_i)|^2 + λ ∫_{x_1}^{x_N} \left[ S''(x) \right]^2 \, \mathrm{d}x
$$

Only cubic splines (`BSplineOrder(4)`) are currently supported. One must explicitly pass `BSplineOrder(4)` as a first argument to avoid collisions with other implementations of `StatsAPI.fit`.

The boundary condition (`bc`) must be [`Periodic`](@ref) for a periodic spline or [`Natural`](@ref) otherwise (this is the default). (Currently, the periodic case can be much slower than the default natural condition.)

# Examples

```jldoctest smoothing_spline
julia> xs = (0:0.01:1).^2;

julia> ys = @. cospi(2 * xs) + 0.1 * sinpi(200 * xs);  # smooth + highly fluctuating components

julia> λ = 0.001;  # smoothing parameter

julia> S = fit(BSplineOrder(4), xs, ys, λ)
101-element Spline{Float64}:
 basis: 101-element RecombinedBSplineBasis of order 4, domain [0.0, 1.0], BCs {left => (D{2},), right => (D{2},)}
 order: 4
 knots: [0.0, 0.0, 0.0, 0.0, 0.0001, 0.0004, 0.0009, 0.0016, 0.0025, 0.0036  …  0.8836, 0.9025, 0.9216, 0.9409, 0.9604, 0.9801, 1.0, 1.0, 1.0, 1.0]
 coefficients: [0.946872, 0.631018, 1.05101, 1.04986, 1.04825, 1.04618, 1.04366, 1.04067, 1.03722, 1.03331  …  0.437844, 0.534546, 0.627651, 0.716043, 0.798813, 0.875733, 0.947428, 1.01524, 0.721199, 0.954231]
```
