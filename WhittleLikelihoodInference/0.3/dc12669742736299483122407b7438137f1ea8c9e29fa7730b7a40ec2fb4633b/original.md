```
WhittleLikelihood(model::Type{<:TimeSeriesModel}, ts, Δ; lowerΩcutoff, upperΩcutoff, taper)
WhittleLikelihood(model::Type{<:TimeSeriesModel}, timeseries::TimeSeries; lowerΩcutoff, upperΩcutoff, taper)
```

Generate a function to evaluate the Whittle likelihood it's gradient and Hessian.

Create a callable struct which prealloctes memory appropriately.

```
(f::WhittleLikelihood)(θ)
```

Evaluates the Whittle likelihood at θ.

```
(f::WhittleLikelihood)(F,G,H,θ)
```

Evaluates the Whittle likelihood at θ and stores the gradient and Hessian in G and H respectively. If F, G or H equal nothing, then the function, gradient or Hessian are not evaluated repsectively.

# Aruguments

  * `model`: the model for the process. Should be of type TimeSeriesModel, so `OU` and not `OU(1,1)`.
  * `ts`: the timeseries in the form of an n by d matrix (where d is the dimension of the time series model).
  * `Δ`: the sampling rate of the time series.
  * `timeseries`: can be provided instead of `ts` and `Δ`. Must be of type `TimeSeries`.
  * `lowerΩcutoff`: the lower bound of the frequency range included in the likelihood.
  * `upperΩcutoff`: the upper bound of the frequency range included in the likelihood.
  * `taper`: optional taper which should be a vector of length `size(ts,1)`, or `nothing` in which case no taper will be used.

Note that to use the gradient the model must have `grad_add_sdf!` specified. Similarly, to use the Hessian, the model must have `hess_add_sdf!` specified.

# Examples

```julia-repl
julia> obj = WhittleLikelihood(OU, ones(1000), 1)
Whittle likelihood for the OU model.

julia> obj([1.0, 1.0])
-2006.7870804551364

julia> F, G, H = 0.0, zeros(2), zeros(2,2)
(0.0, [0.0, 0.0], [0.0 0.0; 0.0 0.0])

julia> obj(F, G, H, [1.0, 1.0])
-2006.7870804551364

julia> G
2-element Vector{Float64}:
   2.777354965282642
 -17.45063591068618

julia> H
2×2 Matrix{Float64}:
 -0.00967179   0.0607696
  0.0607696   -0.381827
```
