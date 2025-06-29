```
SequentialPairDistances <: CountBasedOutcomeSpace
SequentialPairDistances(x::AbstractVector; n = 3, metric = Chebyshev(), m = 3, τ = 1)
SequentialPairDistances(x::AbstractStateSpaceSet; n = 3, metric = Chebyshev())
```

An outcome space based on the distribution of distances of sequential pairs of points.

This outcome space appears implicitly as part of the "distribution entropy" introduced by [Li2015](@citet), which of course can be reproduced here (see example below). We've generalized the method to be used with any [`InformationMeasure`](@ref) and [`DiscreteInfoEstimator`](@ref), and with valid distance `metric` (from Distances.jl).

Input data `x` are needed for initialization, because distances must be pre-computed to know the minimum/maximum distances needed for binning the distribution of pairwise distances. If the input is an `AbstractVector`, then the vector is embedded before computing distances. If the input is an `AbstractStateSpaceSet`, then the embedding step  is skipped and distances are computed directly on each state vector `xᵢ ∈ x`.

## Description

`SequentialPairDistances` does the following: 

  * Transforms the input timeseries `x` by first embedding it using embedding dimension   `m` and embedding lag `τ` (or skip this step if the input is already embedded).
  * Computes the distances `ds` between sequential pairs of points according to the given   `metric`.
  * Divides the interval `[minimum(ds), maximum(ds)]` into `n` equal-size bins by using    [`RectangularBinEncoding`](@ref), then maps the distances onto these bins.

## Outcome space

The outcome space `Ω` for `SequentialPairDistances` are the bins onto which the  pairwise distances are mapped, encoded as the integers `1:n`. If you need the actual bin coordinates, these can be recovered with [`decode`](@ref) (see example below).

## Implements

  * [`codify`](@ref). Note that the input `x` is ignored when calling `codify`, because   the input data is already handled when constructing a `SequentialPairDistances`.

## Examples

The outcome bins can be retrieved as follows.

```julia
using ComplexityMeasures
x = rand(100)
o = SequentialPairDistances(x)
cts, outs = counts_and_outcomes(o, x)
```

Computing the "distribution entropy" with `n = 3` bins for the distance histogram:

```julia
using ComplexityMeasures
x = rand(1000000)
o = SequentialPairDistances(x, n = 3, metric = Chebyshev()) # metric from original paper
h = information(Shannon(base = 2), o, x)
```
