```
ExtendedUnbinnedNLL(data::AbstractArray, scaled_pdf::Function; log=false, verbose=0, mask=nothing, grad=nothing, names=())
```

Unbinned extended negative log-likelihood.

Use this if shape and normalization of the fitted PDF are of interest and the original unbinned data is available. The data can be one- or multi-dimensional.

## Arguments

  * `data::AbstractArray` : Sample of observations. If the observations are multidimensional, data must  have the shape (D, N), where D is the number of dimensions and N the number of data points.
  * `scaled_pdf::Function` : Probability density function of the form f(data, par0, [par1, ...]), where  data is the sample and par0, ... are model parameters. Must return a tuple (<integral  over f in data window>, <f evaluated at data points>). The first value is the density integrated over   the data window, the interval that we consider for the fit. For example, if the data are exponentially distributed, but we  fit only the interval (0, 5), then the first value is the density integrated from 0 to 5.   If the data are multivariate, data passed to f has shape (D,N), where D is the number of dimensions and N the number of data points.
  * `verbose::Int` : Verbosity level. 0: is no output.
  * `log::Bool=false` : Distributions of the exponential family (normal, exponential, poisson, ...)  allow one to compute the logarithm of the pdf directly, which is more  accurate and efficient than numerically computing $log(pdf)$. Set this  to `true`, if the model returns the logpdf instead of the pdf.
  * `mask::Union{Vector{Bool}, BitVector, Nothing}` : Optional mask to select a subset of the data. Must have the same length as data.
  * `grad::Union{Function, Nothing}` : Optionally pass the gradient of the pdf. Has the same calling signature like  the pdf, but must return an array with the shape (K, N), where N is the number of data points and K is the number of parameters.
  * `names` : Optional names for each parameter of the model (in order). Must have the same length as there are model parameters.
