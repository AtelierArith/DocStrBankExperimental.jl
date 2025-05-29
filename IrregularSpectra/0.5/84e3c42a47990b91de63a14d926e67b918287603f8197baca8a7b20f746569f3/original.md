`Prolate1D(bandwidth::Float64, intervals::Vector{NTuple{2,Float64}}, ntaper::Int64)`

A (generalized) prolate function with support on `intervals` and half-bandwidth `bandwidth`. Unlike a closed-form window like the Kaiser, this function and its Fourier transform are only available by numerical solving an integral eigenvalue problem. Because of this, scalar evaluation methods like `(p::Prolate1D)(x)` or `IrregularSpectra.fouriertransform(p::Prolate1D, ω::Float64)` are intentionally not implemented.

`Prolate1D` has the construction method

`Prolate1D(intervals;             bandwidth=default_bandwidth(intervals),            ntaper=default_ntaper(intervals, bandwidth))`

which automatically selects the bandwidth and a number of tapers (potentially greater than 1). When `ntapers>1`, the estimator you will obtain is a multitaper estimator.
