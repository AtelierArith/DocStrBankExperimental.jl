```
RectangularBinning(ϵ)
```

Instructions for creating a rectangular box partition using the binning scheme `ϵ`. 

# Fields

  * **`ϵ`**: A valid binning scheme.

# Valid binning schemes

The following `ϵ` are valid.

## Data ranges along each axis dictated by data ranges

1. `RectangularBinning(ϵ::Int)` divides each axis into `ϵ` equal-length intervals,   extending the upper bound 1/100th of a bin size to ensure all points are covered.
2. `RectangularBinning(ϵ::Float64)` divides each axis into intervals of fixed size `ϵ`.
3. `RectangularBinning(ϵ::Vector{Int})` divides the i-th axis into `ϵᵢ` equal-length   intervals, extending the upper bound 1/100th of a bin size to ensure all points are   covered.
4. `RectangularBinning(ϵ::Vector{Float64})` divides the i-th axis into intervals of size   `ϵ[i]`.

In these cases, the rectangular partition is constructed by locating the minima along each  coordinate axis, then constructing equal-length intervals until the data maxima are covered. 

## Custom ranges along each axis

Rectangular binnings may also be specified on arbitrary min-max ranges. 

5. `RectangularBinning(ϵ::Tuple{Vector{Tuple{Float64,Float64}},Int64})` creates intervals   along each axis from ranges indicated by a vector of `(min, max)` tuples, then divides   each axis into the same integer number of equal-length intervals.

It's probably easier to use the following constructors

  * `RectangularBinning(RectangularBinning(minmaxes::Vararg{<:AbstractRange{T}, N}; n_intervals::Int = 10))` takes a    vector of tuples indiciating the (min, max) along each axis and `n_intervals` that    indicates how many equal-length intervals those ranges should be split into.
  * `RectangularBinning(minmaxes::Vector{<:AbstractRange{T}}, n_intervals::Int)` does the    same, but the arguments are provided as ranges.

# Examples

Minimal and maximal positions of the grid determined by the data points:

  * `RectangularBinning(10)`: find the minima along each coordinate axis of the points, then    split the (extended) range into `10` equal-length intervals.
  * `RectangularBinning([10, 5])`: find the minima along each coordinate axis of the points,    then split the (extended) range along the first coordinate axis into `10` equal-length    intervals and the range along the second coordinate axis into `5` equal-length intervals.
  * `RectangularBinning(0.5)`: find the minima along each coordinate axis of the points, then    split the axis ranges into equal-length intervals of size `0.5`
  * `RectangularBinning([0.3, 0.1])`: find the minima along each coordinate axis of the points, then    split the range along the first coordinate axis into equal-length intervals of size    `0.3` and the range along the second axis into equal-length intervals of size `0.1`.

Explitly specifying data ranges (not guaranteed to cover data points): 

  * `RectangularBinning(-5:5, 2:2, n_intervals = 5)`: split the ranges `-5:5` and `2:2` into    `n_intervals` equal-length intervals.
