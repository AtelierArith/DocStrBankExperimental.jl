```
SpatialDispersion <: OutcomeSpace
SpatialDispersion(stencil, x::AbstractArray;
    periodic = true,
    c = 5,
    skip_encoding = false,
    L = nothing,
)
```

A dispersion-based [`OutcomeSpace`](@ref) that generalises [`Dispersion`](@ref) for input data that are high-dimensional arrays.

`SpatialDispersion` is based on [Azami2019](@citet)'s 2D square dispersion (Shannon) entropy estimator, but is here implemented as a pure probabilities probabilities estimator that is generalized for `N`-dimensional input data `x`, with arbitrary neighborhood regions (stencils) and (optionally) periodic boundary conditions.

In combination with [`information`](@ref) and [`information_normalized`](@ref), this probabilities estimator can be used to compute (normalized) generalized spatiotemporal dispersion [`InformationMeasure`](@ref) of any type.

## Arguments

  * `stencil`. Defines what local area (hyperrectangle), or which points within this area,   to include around each hypervoxel (i.e. pixel in 2D). The examples below demonstrate   different ways of specifying stencils. For details, see   [`SpatialOrdinalPatterns`](@ref). See [`SpatialOrdinalPatterns`](@ref) for   more information about stencils.
  * `x::AbstractArray`. The input data. Must be provided because we need to know its size   for optimization and bound checking.

## Keyword arguments

  * `periodic::Bool`. If `periodic == true`, then the stencil should wrap around at the   end of the array. If `periodic = false`, then pixels whose stencil exceeds the array   bounds are skipped.
  * `c::Int`. Determines how many discrete categories to use for the Gaussian encoding.
  * `skip_encoding`. If `skip_encoding == true`, `encoding` is ignored, and dispersion   patterns are computed directly from `x`, under the assumption that `L` is the alphabet   length for `x` (useful for categorical or integer data). Thus, if   `skip_encoding == true`, then `L` must also be specified. This is useful for   categorical or integer-valued data.
  * `L`. If `L == nothing` (default), then the number of total outcomes is inferred from   `stencil` and `encoding`. If `L` is set to an integer, then the data is considered   pre-encoded and the number of total outcomes is set to `L`.

## Outcome space

The outcome space for `SpatialDispersion` is the unique delay vectors whose elements are the the symbols (integers) encoded by the Gaussian CDF. Hence, the outcome space is all `m`-dimensional delay vectors whose elements are all possible values in `1:c`. There are `c^m` such vectors.

## Description

Estimating probabilities/entropies from higher-dimensional data is conceptually simple.

1. Discretize each value (hypervoxel) in `x` relative to all other values `xᵢ ∈ x` using the  provided `encoding` scheme.
2. Use `stencil` to extract relevant (discretized) points around each hypervoxel.
3. Construct a symbol these points.
4. Take the sum-normalized histogram of the symbol as a probability distribution.
5. Optionally, compute [`information`](@ref) or [`information_normalized`](@ref) from this  probability distribution.

## Usage

Here's how to compute spatial dispersion entropy using the three different ways of specifying stencils.

```julia
x = rand(50, 50) # first "time slice" of a spatial system evolution

# Cartesian stencil
stencil_cartesian = CartesianIndex.([(0,0), (1,0), (1,1), (0,1)])
est = SpatialDispersion(stencil_cartesian, x)
information_normalized(est, x)

# Extent/lag stencil
extent = (2, 2); lag = (1, 1); stencil_ext_lag = (extent, lag)
est = SpatialDispersion(stencil_ext_lag, x)
information_normalized(est, x)

# Matrix stencil
stencil_matrix = [1 1; 1 1]
est = SpatialDispersion(stencil_matrix, x)
information_normalized(est, x)
```

To apply this to timeseries of spatial data, simply loop over the call (broadcast), e.g.:

```julia
imgs = [rand(50, 50) for i = 1:100]; # one image per second over 100 seconds
stencil = ((2, 2), (1, 1)) # a 2x2 stencil (i.e. dispersion patterns of length 4)
est = SpatialDispersion(stencil, first(imgs))
h_vs_t = information_normalized.(Ref(est), imgs)
```

Computing generalized spatiotemporal dispersion entropy is trivial, e.g. with [`Renyi`](@ref):

```julia
x = reshape(repeat(1:5, 500) .+ 0.1*rand(500*5), 50, 50)
est = SpatialDispersion(stencil, x)
information(Renyi(q = 2), est, x)
```

See also: [`SpatialOrdinalPatterns`](@ref), [`GaussianCDFEncoding`](@ref), [`codify`](@ref).
