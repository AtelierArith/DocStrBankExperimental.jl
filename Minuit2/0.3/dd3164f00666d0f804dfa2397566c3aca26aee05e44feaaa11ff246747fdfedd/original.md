```
LeastSquares(x::AbstractArray, y::AbstractVector, yerror, model::Function; 
                 loss=:linear, verbose=0, model_grad=nothing, names=(), mask=nothing)
```

Least-squares cost function (aka chisquare function).

Use this if you have data of the form (x, y +/- yerror), where x can be one-dimensional or multi-dimensional,  but y is always one-dimensional.

## Arguments

  * `x::AbstractArray` : Locations where the model is evaluated. If the model is multivariate, x must       have shape (D, N), where D is the number of dimensions and N the number of data points.
  * `y::AbstractVector` : Observed values. Must have the same length as x.
  * `yerror` : Estimated uncertainty of observed values. Must have same shape as y or be a  scalar, which is then broadcasted to same shape as y.
  * `model::Function` : Function of the form f(x, par0, [par1, ...]) whose output is compared to  observed values, where x is the location and par0, ... are model parameters. If the model is multivariate,   x has shape (D,), where D is the N the number of data points.
  * `loss::Union{Symbol, Function}` : The loss function can be modified to make the fit robust against outliers. Only ``:linear` and `:soft_l1` are currently implemented, but users can pass any loss function as this argument. It should be a monotonic, twice differentiable function,  which accepts the squared residual and returns a modified squared residual.
  * `verbose::Int` :  Verbosity level. 0: is no output.
  * `model_grad::Union{Function, Nothing}` : Optionally pass the gradient of the model. Has the same calling signature like the model, but must return an array with the shape (K,), where K is the number of parameters.  The gradient can be used by Minuit to improve or speed up convergence.
  * `names` : Optional names for each parameter of the model (in order). Must have the same length as there are model parameters.
  * `mask::Union{Vector{Bool}, BitVector, Nothing}` : Optional mask to select a subset of the data. Must have the same length as x.

## Notes

Alternative loss functions make the fit more robust against outliers by weakening the pull of outliers. The mechanical analog of a least-squares fit is a system with attractive forces. The loss function can be modified to make the fit robust against outliers.
