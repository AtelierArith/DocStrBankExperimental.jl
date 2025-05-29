```
RegularDownsampling <: MultiScaleAlgorithm
RegularDownsampling(; f::Function = Statistics.mean, scales = 1:8)
```

The original multi-scale algorithm for multiscale entropy analysis [Costa2002](@cite), which yields a single downsampled time series per scale `s`.

## Description

Given a scalar-valued input time series `x`, the `Regular` multiscale algorithm downsamples and coarse-grains `x` by splitting it into non-overlapping windows of length `s`, and then constructing a new downsampled time series $D_t(s, f)$ by applying the function `f` to each of the resulting length-`s` windows.

The downsampled time series `D_t(s)` with `t ∈ [1, 2, …, L]`, where `L = floor(N / s)`, is given by:

$$
\{ D_t(s, f)  \}_{t = 1}^{L} = \left\{ f \left( \bf x_t \right) \right\}_{t = 1}^{L} =
\left\{
    {f\left( (x_i)_{i = (t - 1)s + 1}^{ts} \right)}
\right\}_{t = 1}^{L}
$$

where `f` is some summary statistic applied to the length-`ts-((t - 1)s + 1)` tuples `xₖ`. Different choices of `f` have yield different multiscale methods appearing in the literature. For example:

  * `f == Statistics.mean` yields the original first-moment multiscale sample entropy   [Costa2002](@cite).
  * `f == Statistics.var` yields the generalized multiscale sample entropy [Costa2015](@cite),   which uses the second-moment (variance) instead of the mean.

## Keyword Arguments

  * **`scales`**. The downsampling levels. If `scales` is set to an integer, then this integer   is taken as maximum number of scales (i.e. levels of downsampling), and downsampling   is done over levels `1:scales`. Otherwise, downsampling is done over the provided   `scales` (which may be a range, or some specific scales (e.g. `scales = [1, 5, 6]`).   The maximum scale level is `length(x) ÷ 2`, but to avoid applying the method to time   series that are extremely short, consider limiting the maximum scale  (e.g.   `scales = length(x) ÷ 5`).

See also: [`CompositeDownsampling`](@ref).
