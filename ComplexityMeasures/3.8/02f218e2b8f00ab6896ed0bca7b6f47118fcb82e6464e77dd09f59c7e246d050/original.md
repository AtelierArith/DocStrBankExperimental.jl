```
CompositeDownsampling <: MultiScaleAlgorithm
CompositeDownsampling(; f::Function = Statistics.mean, scales = 1:8)
```

Composite multi-scale algorithm for multiscale entropy analysis [Wu2013](@cite), used with [`multiscale`](@ref) to compute, for example, composite multiscale entropy (CMSE).

## Description

Given a scalar-valued input time series `x`, the composite multiscale algorithm, like [`RegularDownsampling`](@ref), downsamples and coarse-grains `x` by splitting it into non-overlapping windows of length `s`, and then constructing downsampled time series by applying the function `f` to each of the resulting length-`s` windows.

However, [Wu2013](@citet) realized that for each scale `s`, there are actually `s` different ways of selecting windows, depending on where indexing starts/ends. These `s` different downsampled time series `D_t(s, f)` at each scale `s` are constructed as follows:

$$
\{ D_{k}(s) \} = \{ D_{t, k}(s) \}_{t = 1}^{L}, = \{ f \left( \bf x_{t, k} \right) \} =
\left\{
    {f\left( (x_i)_{i = (t - 1)s + k}^{ts + k - 1} \right)}
\right\}_{t = 1}^{L},
$$

where `L = floor((N - s + 1) / s)` and `1 ≤ k ≤ s`, such that $D_{i, k}(s)$ is the `i`-th element of the `k`-th downsampled time series at scale `s`.

Finally, compute $\dfrac{1}{s} \sum_{k = 1}^s g(D_{k}(s))$, where `g` is some summary function, for example [`information`](@ref) or [`complexity`](@ref).

## Keyword Arguments

  * **`scales`**. The downsampling levels. If `scales` is set to an integer, then this integer   is taken as maximum number of scales (i.e. levels of downsampling), and downsampling   is done over levels `1:scales`. Otherwise, downsampling is done over the provided   `scales` (which may be a range, or some specific scales (e.g. `scales = [1, 5, 6]`).   The maximum scale level is `length(x) ÷ 2`, but to avoid applying the method to time   series that are extremely short, consider limiting the maximum scale  (e.g.   `scales = length(x) ÷ 5`).

!!! note "Relation to RegularDownsampling"
    The downsampled time series $D_{t, 1}(s)$ constructed using the composite multiscale method is equivalent to the downsampled time series $D_{t}(s)$ constructed using the [`RegularDownsampling`](@ref) method, for which `k == 1` is fixed, such that only a single time series is returned.


See also: [`RegularDownsampling`](@ref).
