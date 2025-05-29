```
BinnedNLL(bincounts::AbstractArray, binedges::Union{AbstractArray, Tuple}, cdf::Function; use_pdf=:none, verbose=0,  grad=nothing, names=())
```

Binned negative log-likelihood.

Use this if only the shape of the fitted PDF is of interest and the data is binned. This cost function works with normal and weighted histograms.  The histogram can be one- or multi-dimensional.

## Arguments

  * `bincounts::AbstractArray` : Histogram counts. If this is an array with dimension D, where D is the number of histogram axes.
  * `xe::Union{AbstractArray, Tuple}` : Bin edge locations, must be len(n) + 1, where n is the number of bins.  If the histogram has more than one axis, xe must be a collection of the bin edge locations along each axis.
  * `cdf::Function` : Cumulative density function of the form f(xe, par0, par1, ..., parN),  where xe is a bin edge and par0, ... are model parameters. The corresponding density must be normalized to unity   over the space covered by the histogram. If the model is multivariate, xe must be an array-like with shape (D, N),  where D is the dimension and N is the number of points where the model is evaluated.
  * `verbose::Int` : Verbosity level. 0: is no output.
  * `grad::Union{Function, Nothing} : Optionally pass the gradient of the`cdf``. Has the same calling signature like the cdf,   but must return an array with the shape (K,), where K is the number of parameters. The gradient can be used by Minuit to   improve or speed up convergence.
  * `use_pdf::Symbol`: Either `:none`, `:numerical`, or `:approximate`. If the model cdf is not available, but the model pdf is,   this option can be set to "numerical" or "approximate" to compute the integral of the pdf over the bin. The option "numerical"   uses numerical integration, which is accurate but computationally expensive and only supported for 1D histograms. The  option "approximate" uses the zero-order approximation of evaluating the pdf at the bin center, multiplied with the bin area.  This is fast and works in higher dimensions, but can lead to biased results if the curvature of the pdf inside the bin is significant.
  * `names` : Optional names for each parameter of the model (in order). Must have the same length as there are model parameters.
