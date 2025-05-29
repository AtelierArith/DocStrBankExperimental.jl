TaylorSpectral(param, index::NTuple{N}, freq0::Real, p0=zero(param))

Creates a frequency model that expands the parameter in a Taylor series defined by      `param * exp(∑ₙ index[n] * log(Fr / freq0)^n)` + p0. i.e. an expansion in log(Fr / freq0) where Fr is the frequency of the observation,  `freq0` is the reference frequency, `param` is the parameter value at `freq0`. You can optionally add a constant term `p0` to the expansion that defines the zeroth order term or offset.

The `N` in index defines the order of the Taylor expansion. If `index` is a `<:Real` then the expansion is of order 1.
