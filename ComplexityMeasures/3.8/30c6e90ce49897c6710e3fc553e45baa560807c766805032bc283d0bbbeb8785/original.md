```
OrdinalPatterns <: OutcomeSpace
OrdinalPatterns{m}(τ = 1, lt::Function = ComplexityMeasures.isless_rand)
```

An [`OutcomeSpace`](@ref) based on lengh-`m` ordinal permutation patterns, originally introduced in [BandtPompe2002](@citet)'s paper on permutation entropy. Note that `m` is given as a type parameter, so that when it is a literal integer there are performance accelerations.

When passed to [`probabilities`](@ref) the output depends on the input data type:

  * **Univariate data**. If applied to a univariate timeseries (`AbstractVector`), then the timeseries   is first embedded using embedding delay `τ` and dimension `m`, resulting in embedding   vectors $\{ \bf{x}_i \}_{i=1}^{N-(m-1)\tau}$. Then, for each $\bf{x}_i$,   we find its permutation pattern $\pi_{i}$. Probabilities are then   estimated as the frequencies of the encoded permutation symbols   by using [`UniqueElements`](@ref). When giving the resulting probabilities to   [`information`](@ref), the original permutation entropy is computed [BandtPompe2002](@cite).
  * **Multivariate data**. If applied to a an `D`-dimensional `StateSpaceSet`,   then no embedding is constructed, `m` must be equal to `D` and `τ` is ignored.   Each vector $\bf{x}_i$ of the dataset is mapped   directly to its permutation pattern $\pi_{i}$ by comparing the   relative magnitudes of the elements of $\bf{x}_i$.   Like above, probabilities are estimated as the frequencies of the permutation symbols.   The resulting probabilities can be used to compute multivariate permutation   entropy [He2016](@cite), although here we don't perform any further subdivision   of the permutation patterns (as in Figure 3 of [He2016](@citet)).

Internally, [`OrdinalPatterns`](@ref) uses the [`OrdinalPatternEncoding`](@ref) to represent ordinal patterns as integers for efficient computations.

See [`WeightedOrdinalPatterns`](@ref) and [`AmplitudeAwareOrdinalPatterns`](@ref) for estimators that not only consider ordinal (sorting) patterns, but also incorporate information about within-state-vector amplitudes. For a version of this estimator that can be used on spatial data, see [`SpatialOrdinalPatterns`](@ref).

!!! note "Handling equal values in ordinal patterns"
    In [BandtPompe2002](@citet), equal values are ordered after their order of appearance, but this can lead to erroneous temporal correlations, especially for data with low amplitude resolution [Zunino2017](@cite). Here, by default, if two values are equal, then one of the is randomly assigned as "the largest", using `lt = ComplexityMeasures.isless_rand`. To get the behaviour from [BandtPompe2002](@citet), use `lt = Base.isless`.


## Outcome space

The outcome space `Ω` for `OrdinalPatterns` is the set of length-`m` ordinal patterns (i.e. permutations) that can be formed by the integers `1, 2, …, m`. There are `factorial(m)` such patterns.

For example, the outcome `[2, 3, 1]` corresponds to the ordinal pattern of having the smallest value in the second position, the next smallest value in the third position, and the next smallest, i.e. the largest value in the first position. See also [`OrdinalPatternEncoding`](@ref).

## In-place symbolization

`OrdinalPatterns` also implements the in-place [`probabilities!`](@ref) for `StateSpaceSet` input (or embedded vector input) for reducing allocations in looping scenarios. The length of the pre-allocated symbol vector must be the length of the dataset. For example

```julia
using ComplexityMeasures
m, N = 2, 100
est = OrdinalPatterns{m}(τ)
x = StateSpaceSet(rand(N, m)) # some input dataset
πs_ts = zeros(Int, N) # length must match length of `x`
p = probabilities!(πs_ts, est, x)
```
