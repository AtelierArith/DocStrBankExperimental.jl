```
Histogram <: AbstractHistogram
```

The `Histogram` type represents data that has been tabulated into intervals (known as *bins*) along the real line, or in higher dimensions, over a real space. Histograms can be fitted to data using the `fit` method.

# Fields

  * edges: An iterator that contains the boundaries of the bins in each dimension.
  * weights: An array that contains the weight of each bin.
  * closed: A symbol with value `:right` or `:left` indicating on which side bins (half-open intervals or higher-dimensional analogues thereof) are closed. See below for an example.
  * isdensity: There are two interpretations of a `Histogram`. If `isdensity=false` the weight of a bin corresponds to the amount of a quantity in the bin. If `isdensity=true` then it corresponds to the density (amount / volume) of the quantity in the bin. See below for an example.

# Examples

## Example illustrating `closed`

```jldoctest
julia> using StatsBase

julia> fit(Histogram, [2.],  1:3, closed=:left)
Histogram{Int64, 1, Tuple{UnitRange{Int64}}}
edges:
  1:3
weights: [0, 1]
closed: left
isdensity: false

julia> fit(Histogram, [2.],  1:3, closed=:right)
Histogram{Int64, 1, Tuple{UnitRange{Int64}}}
edges:
  1:3
weights: [1, 0]
closed: right
isdensity: false
```

## Example illustrating `isdensity`

```julia
julia> using StatsBase, LinearAlgebra

julia> bins = [0,1,7]; # a small and a large bin

julia> obs = [0.5, 1.5, 1.5, 2.5]; # one observation in the small bin and three in the large

julia> h = fit(Histogram, obs, bins)
Histogram{Int64,1,Tuple{Array{Int64,1}}}
edges:
  [0, 1, 7]
weights: [1, 3]
closed: left
isdensity: false

julia> # observe isdensity = false and the weights field records the number of observations in each bin

julia> normalize(h, mode=:density)
Histogram{Float64,1,Tuple{Array{Int64,1}}}
edges:
  [0, 1, 7]
weights: [1.0, 0.5]
closed: left
isdensity: true

julia> # observe isdensity = true and weights tells us the number of observation per binsize in each bin
```
