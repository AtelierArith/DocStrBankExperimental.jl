```
FixedRectangularBinning <: AbstractBinning
FixedRectangularBinning(ranges::Tuple{<:AbstractRange...}, precise = false)
```

Rectangular box partition of state space where the partition along each dimension is explicitly given by each range `ranges`, which is a tuple of `AbstractRange` subtypes. Typically, each range is the output of the `range` Base function, e.g., `ranges = (0:0.1:1, range(0, 1; length = 101), range(2.1, 3.2; step = 0.33))`. All ranges must be sorted.

The optional second argument `precise` dictates whether Julia Base's `TwicePrecision` is used for when searching where a point falls into the range. Useful for edge cases of points being almost exactly on the bin edges, but it is exactly four times as slow, so by default it is `false`.

Points falling outside the partition do not contribute to probabilities. Bins are always left-closed-right-open: `[a, b)`. **This means that the last value of each of the ranges dictates the last right-closing value.** This value does *not* belong to the histogram! E.g., if given a range `r = range(0, 1; length = 11)`, with `r[end] = 1`, the value `1` is outside the partition and would not attribute any increase of the probability corresponding to the last bin (here `[0.9, 1)`)!

**Equivalently, the size of the histogram is `histsize = map(r -> length(r)-1, ranges)`!**

`FixedRectangularBinning` leads to a well-defined outcome space without knowledge of input data, see [`ValueBinning`](@ref).
