```
ValueBinning(b::AbstractBinning) <: OutcomeSpace
```

An [`OutcomeSpace`](@ref) based on binning the values of the data as dictated by the binning scheme `b` and formally computing their histogram, i.e., the frequencies of points in the bins. An alias to this is `VisitationFrequency`. Available binnings are subtypes of [`AbstractBinning`](@ref).

The `ValueBinning` estimator has a linearithmic time complexity (`n log(n)` for `n = length(x)`) and a linear space complexity (`l` for `l = dimension(x)`). This allows computation of probabilities (histograms) of high-dimensional datasets and with small box sizes `ε` without memory overflow and with maximum performance. For performance reasons, the probabilities returned never contain 0s and are arbitrarily ordered.

```
ValueBinning(ϵ::Union{Real,Vector})
```

A convenience method that accepts same input as [`RectangularBinning`](@ref) and initializes this binning directly.

## Outcomes

The outcome space for `ValueBinning` is the unique bins constructed from `b`. Each bin is identified by its left (lowest-value) corner, because bins are always left-closed-right-open intervals `[a, b)`. The bins are in data units, not integer (cartesian indices units), and are returned as `SVector`s, i.e., same type as input data.

For convenience, [`outcome_space`](@ref) returns the outcomes in the same array format as the underlying binning (e.g., `Matrix` for 2D input).

For [`FixedRectangularBinning`](@ref) the [`outcome_space`](@ref) is well-defined from the binning, but for [`RectangularBinning`](@ref) input `x` is needed as well.

## Implements

  * [`codify`](@ref). Used for encoding inputs where ordering matters (e.g. time series).
