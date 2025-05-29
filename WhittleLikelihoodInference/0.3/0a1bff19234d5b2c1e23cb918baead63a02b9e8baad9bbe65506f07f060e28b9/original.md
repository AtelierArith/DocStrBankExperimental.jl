```
DebiasedWhittleLikelihood(model::Type{<:TimeSeriesModel}, ts, Δ; lowerΩcutoff, upperΩcutoff, taper)
DebiasedWhittleLikelihood(model::Type{<:TimeSeriesModel}, timeseries::TimeSeries; lowerΩcutoff, upperΩcutoff, taper)
```

Generate a function to evaluate the Debiased Whittle likelihood it's gradient and expected Hessian.

Create a callable struct which prealloctes memory appropriately.

```
(f::DebiasedWhittleLikelihood)(θ)
```

Evaluates the Whittle likelihood at θ.

```
(f::DebiasedWhittleLikelihood)(F,G,EH,θ)
```

Evaluates the Whittle likelihood at θ and stores the gradient and expected Hessian in G and EH respectively. If F, G or EH equal nothing, then the function, gradient or expected Hessian are not evaluated repsectively.

# Aruguments

  * `model`: the model for the process. Should be of type TimeSeriesModel, so `OU` and not `OU(1,1)`.
  * `ts`: the timeseries in the form of an n by d matrix (where d is the dimension of the time series model).
  * `Δ`: the sampling rate of the time series.
  * `timeseries`: can be provided instead of `ts` and `Δ`. Must be of type `TimeSeries`.
  * `lowerΩcutoff`: the lower bound of the frequency range included in the likelihood.
  * `upperΩcutoff`: the upper bound of the frequency range included in the likelihood.
  * `taper`: optional taper which should be a vector of length `size(ts,1)`, or `nothing` in which case no taper will be used.

Note that to use the gradient the model must have `grad_add_sdf!` or `grad_acv!` specified. Similarly, to use the Hessian, the model must have `hess_add_sdf!` or `hess_acv!` specified.

# Examples

```julia-repl
julia> obj = DebiasedWhittleLikelihood(OU, ones(1000), 1)
Debiased Whittle likelihood for the OU model.

julia> obj([1.0, 1.0])
-1982.0676530999626

julia> F, G, EH = 0.0, zeros(2), zeros(2,2)
(0.0, [0.0, 0.0], [0.0 0.0; 0.0 0.0])

julia> obj(F, G, EH, [1.0, 1.0])
-1982.0676530999626

julia> G
2-element Vector{Float64}:
 1998.3136810970122
 -685.7904154568779

julia> H
2×2 Matrix{Float64}:
 -0.00967179   0.0607696
  0.0607696   -0.381827
```
