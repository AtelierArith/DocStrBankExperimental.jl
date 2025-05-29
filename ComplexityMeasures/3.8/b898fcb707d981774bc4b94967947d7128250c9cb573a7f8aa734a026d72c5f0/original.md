```
InformationMeasure
```

`InformationMeasure` is the supertype of all information measure *definitions*.

In this package, we define "information measures" as functionals of probability mass functions ("discrete" measures), or of probability density functions ("differential" measures). Examples are (generalized) entropies such as [`Shannon`](@ref) or [`Renyi`](@ref), or extropies like [`ShannonExtropy`](@ref). [Amigó2018](@citet) provides a useful review of generalized entropies.

## Used with

Any of the information measures listed below can be used with

  * [`information`](@ref), to compute a numerical value for the measure, given some input data.
  * [`information_maximum`](@ref), to compute the maximum possible value for the measure.
  * [`information_normalized`](@ref), to compute the normalized form of the   measure (divided by the maximum possible value).

The [`information_maximum`](@ref)/[`information_normalized`](@ref) functions only works with the discrete version of the measure. See docstrings for the above functions for usage examples.

## Implementations

  * [`Renyi`](@ref).
  * [`Tsallis`](@ref).
  * [`Shannon`](@ref), which is a subcase of the above two in the limit `q → 1`.
  * [`Kaniadakis`](@ref).
  * [`Curado`](@ref).
  * [`StretchedExponential`](@ref).
  * [`RenyiExtropy`](@ref).
  * [`TsallisExtropy`](@ref).
  * [`ShannonExtropy`](@ref), which is a subcase of the above two in the limit `q → 1`.
  * [`FluctuationComplexity`](@ref).

## Estimators

A particular information measure may have both a discrete and a continuous/differential definition, which are estimated using a [`DifferentialInfoEstimator`](@ref) or a [`DifferentialInfoEstimator`](@ref), respectively.
