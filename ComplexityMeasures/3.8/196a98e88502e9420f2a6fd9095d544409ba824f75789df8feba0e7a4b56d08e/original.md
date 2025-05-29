```
information([die::DiscreteInfoEstimator,] [est::ProbabilitiesEstimator,] o::OutcomeSpace, x) → h::Real
information(o::OutcomeSpace, x) → h::Real
```

Estimate a discrete information measure from input data `x` using the provided [`DiscreteInfoEstimator`](@ref) and [`ProbabilitiesEstimator`](@ref) over the given [`OutcomeSpace`](@ref).

As an alternative, you can provide an [`InformationMeasure`](@ref) for the first argument (`die`) which will default to [`PlugIn`](@ref) estimation) for the information estimation. You may also skip the first argument (`die`), in which case `Shannon()` will be used. You may also skip the second argument (`est`), which will default to the [`RelativeAmount`](@ref) probabilities estimator. Note that some information measure estimators (e.g., [`GeneralizedSchuermann`](@ref)) operate directly on counts and hence ignore `est`.

```
information([e::DiscreteInfoEstimator,] p::Probabilities) → h::Real
information([e::DiscreteInfoEstimator,] c::Counts) → h::Real
```

Like above, but estimate the information measure from the pre-computed [`Probabilities`](@ref) `p` or [`Counts`](@ref). Counts are converted into probabilities using [`RelativeAmount`](@ref), unless the estimator `e` uses counts directly.

See also: [`information_maximum`](@ref), [`information_normalized`](@ref) for a normalized version.

## Examples (naive estimation)

The simplest way to estimate a discrete measure is to provide the [`InformationMeasure`](@ref) directly in combination with an [`OutcomeSpace`](@ref). This will use the "naive" [`PlugIn`](@ref) estimator for the measure, and the "naive" [`RelativeAmount`](@ref) estimator for the probabilities.

```julia
x = randn(100) # some input data
o = ValueBinning(RectangularBinning(5)) # a 5-bin histogram outcome space
h_s = information(Shannon(), o, x)
```

Here are some more examples:

```julia
x = [rand(Bool) for _ in 1:10000] # coin toss
ps = probabilities(x) # gives about [0.5, 0.5] by definition
h = information(ps) # gives 1, about 1 bit by definition (Shannon entropy by default)
h = information(Shannon(), ps) # syntactically equivalent to the above
h = information(Shannon(), UniqueElements(), x) # syntactically equivalent to above
h = information(Renyi(2.0), ps) # also gives 1, order `q` doesn't matter for coin toss
h = information(OrdinalPatterns(;m=3), x) # gives about 2, again by definition
```

## Examples (bias-corrected estimation)

It is known that both [`PlugIn`](@ref) estimation for information measures and [`RelativeAmount`](@ref) estimation for probabilities are biased. The scientific literature abounds with estimators that correct for this bias, both on the measure-estimation level and on the probability-estimation level. We thus provide the option to use any [`DiscreteInfoEstimator`](@ref) in combination with any [`ProbabilitiesEstimator`](@ref) for improved estimates. Note that custom probabilites estimators will only work with counting-compatible [`OutcomeSpace`](@ref).

```julia
x = randn(100)
o = ValueBinning(RectangularBinning(5))

# Estimate Shannon entropy estimation using various dedicated estimators
h_s = information(MillerMadow(Shannon()), RelativeAmount(), o, x)
h_s = information(HorvitzThompson(Shannon()), Shrinkage(), o, x)
h_s = information(Schuermann(Shannon()), Shrinkage(), o, x)

# Estimate information measures using the generic `Jackknife` estimator
h_r = information(Jackknife(Renyi()), Shrinkage(), o, x)
j_t = information(Jackknife(TsallisExtropy()), BayesianRegularization(), o, x)
j_r = information(Jackknife(RenyiExtropy()), RelativeAmount(), o, x)
```
