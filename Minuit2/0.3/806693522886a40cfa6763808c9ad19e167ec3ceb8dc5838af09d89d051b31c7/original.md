```
UnbinnedNLL(data::AbstractArray, pdf::Function; log=false, verbose=0, mask=nothing, grad=nothing, names=())
```

Unbinned negative log-likelihood cost function.

## Arguments

  * `data::AbstractArray` : Sample of observations. If the observations are multidimensional, data must have the shape (D, N), where D is the number of dimensions and N the number of data points.
  * `pdf::Function` : Probability density function of the form f(data, par0, [par1, ...]), where data is the data sample and par0, ... are model parameters. If the data are multivariate, data passed to f has shape (D,), where D is the number of dimensions and N the number of data points.
  * `verbose::Int` : Verbosity level. 0: is no output (default). 1: print current args and negative log-likelihood value.
  * `log::Bool=false` : Distributions of the exponential family (normal, exponential, poisson, ...) allow one to compute the logarithm of the pdf directly, which is more accurate and efficient than numerically computing $log(pdf)$. Set this to `true`, if the model returns the logpdf instead of the pdf.
  * `mask::Union{Vector{Bool}, BitVector, Nothing}` : Optional mask to select a subset of the data. Must have the same length as data.
  * `grad::Union{Function, Nothing}` : Optionally pass the gradient of the pdf. Has the same calling signature like the pdf, but must return an array with the shape (K, N), where N is the number of data points and K is the number of parameters. If `log` is True, the function must return the gradient of the logpdf instead of the pdf. The gradient can be used by Minuit to improve or speed up convergence and to compute the sandwich estimator for the variance of the parameter estimates.
  * `names` : Optional names for each parameter of the model (in order). Must have the same length as there are model parameters.

## Returns

  * Cost function object.
