```
multiscale(algorithm::MultiScaleAlgorithm, [args...], x)
```

A convenience function to compute the multiscale version of any [`InformationMeasureEstimator`](@ref) or [`ComplexityEstimator`](@ref)

The return type of `multiscale` is either a `Vector{Real}` or a `Vector{Vector{Real}}`, see the available coarse-graining methods below.

It utilizes [`downsample`](@ref) with the given `algorithm` to first produce coarse-grained, downsampled versions of `x` for scale factors `algorithm.scales`. Then, [`information`](@ref) or [`complexity`](@ref), depending on the input arguments, is applied to each of the coarse-grained timeseries. If `N = length(x)`, then the length of the most severely downsampled version of `x` is `N ÷ maximum(algorithm.scales)`, while for scale factor `1`, the original time series is considered.

## Description

This function generalizes the multiscale entropy of [Costa2002](@cite) to any discrete information measure, any differential information measure, and any other complexity measure.

## Coarse-graining algorithms

The available downsampling routines are:

  * [`RegularDownsampling`](@ref) yields a single `Vector` per scale.
  * [`CompositeDownsampling`](@ref) yields a `Vector{Vector}` per scale.

## Examples

`multiscale` can be used with any discrete or differential information measure estimator. For example, here's two ways of computing multiscale Tsallis entropy:

```julia
using ComplexityMeasures
x = randn(1000)
downsampling = RegularDownsampling(scales = 1:5) # multiscale algorithm

# Symbolic (ordinal-pattern-based) probabilities estimation using Bayesian regularization,
# jackknife estimation of the entropy.
o = OrdinalPatterns{3}(2) # outcome space
probest = BayesianRegularization() # probabilities estimator
hest = Jackknife(Tsallis(q = 1.5)) # entropy estimator
multiscale(downsampling, hest, probest, o, x)

# Differential kNN-based estimator:
hest = LeonenkoProzantoSavani(Tsallis(q = 1.5), k = 10) # 10 neighbors
multiscale(downsampling, hest, x)
```

Multiscale variants of any [`ComplexityEstimator`](@ref) are also trivial to compute. Let's compute the "generalized multiscale sample entropy [Costa2015](@cite)" using the second-order moment.

```julia
using ComplexityMeasures, Statistics
multiscale(CompositeDownsampling(; f = Statistics.var), SampleEntropy(x), x)
```
