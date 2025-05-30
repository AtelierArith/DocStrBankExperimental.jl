Expand given scattering matrix (6-independent columns: a1, a2, a3, a4, b1, b2) to General Spherical Function (GSF) coefficients.

```julia
expand(
    F,
    θ₀;
    smax,
    smin,
    ngauss,
    double_threshold,
    adding_step,
    stop_threshold,
    cutoff,
    interpolation_strategy,
    ε,
    θₑ,
    error_type,
    _kwargs...
)

```

  * `F`: The scattering matrix columns, which should be an `Nθ x 6` matrix.
  * `θ₀`: The scattering angles. If the maximum value is larger than `π`, then the angles are assumed to be in degrees, otherwise the angles are assumed to be in radians.

Optional parameters:

  * `smax`: Highest level for expansion. Default is `-1`, and in such case, the highest level is determined via trial-and-error until the desired precision (defined by `ε` and `error_type`) is reached.
  * `smin`: The start point of iteration. Default is `30`.
  * `ngauss`: The function for determine the number of Gaussian quadrature points. It takes the current expansion level plus 1, `s + 1`, as the input. Default is `identity`.
  * `double_threshold`: The highest level before which `s` is doubled each time. Default is `5000`.
  * `adding_step`: The step size in the adding phase. Default is `100`.
  * `stop_threshold`: The highest permitted expansion level. Default is `20000`.
  * `interpolation_strategy`: The interpolation strategy. Default is `PolarizedBRF.Linear`, which uses `LinearInterpolation` from `Interpolations.jl`. Optional is `PolarizedBRF.Spline`, which uses `Spline1D` from `Dierckx.jl`.
  * `cutoff`: Cut off the expansion coefficients when the absolute value of `α₁` at this level is smaller than `cutoff`. Default is `0.0`, meaning no cutoff will be applied. Note that Ito et al. (2018) used `cutoff = 1e-8`.
  * `ε`: The desired error bound. Default is `0.02`.
  * `θₑ`: The angles used for error checking. Default is `θ₀`.
  * `error_type`: The error type. Default is `PolarizedBRF.AbsoluteError`, other options include `PolarizedBRF.RelativeError` and `PolarizedBRF.RootMeanSquaredError`.
