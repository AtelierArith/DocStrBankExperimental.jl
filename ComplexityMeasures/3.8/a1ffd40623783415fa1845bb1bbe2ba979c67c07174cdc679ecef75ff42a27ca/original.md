```
StatisticalComplexity <: ComplexityEstimator
StatisticalComplexity(; kwargs...)
```

An estimator for the statistical complexity and entropy, originally by [Rosso2007](@cite) and generalized by [Rosso2013](@citet).

Our implementation extends the generalization to any valid distance metric, any [`OutcomeSpace`](@ref) with a priori known [`total_outcomes`](@ref), any [`ProbabilitiesEstimator`](@ref), and any normalizable discrete [`InformationMeasure`](@ref).

Used with [`complexity`](@ref).

## Keyword arguments

  * `o::OutcomeSpace = OrdinalPatterns{3}()`. The [`OutcomeSpace`](@ref), which controls how   the input data are discretized.
  * `pest::ProbabilitiesEstimator = RelativeAmount()`: The   [`ProbabilitiesEstimator`](@ref) used to estimate probabilities over the discretized   input data.
  * `hest = Renyi()`: A [`DiscreteInfoEstimator`](@ref) or an [`InformationMeasure`](@ref).   Any information   measure that defines [`information_maximum`](@ref) is valid here including extropies.   The measure will be estimated using the [`PlugIn`](@ref) estimator if not given an   estimator.
  * `dist <: SemiMetric = JSDivergence()`: The distance measure (from Distances.jl) to use for   estimating the distance between the estimated probability distribution and a uniform   distribution with the same maximal number of outcomes.

## Description

Statistical complexity is defined as

$$
C_q[P] = \mathcal{H}_q\cdot \mathcal{Q}_q[P],
$$

where $Q_q$ is a "disequilibrium" obtained from a distance-measure and $H_q$ a disorder measure. In the original paper[Rosso2007](@cite), this complexity measure was defined via an ordinal pattern-based probability distribution (see [`OrdinalPatterns`](@ref)), using [`Shannon`](@ref) entropy as the information measure, and the Jensen-Shannon divergence as a distance measure.

Our implementation is a further generalization of the complexity measure developed in [Rosso2013](@citet). We let $H_q$be any normalizable [`InformationMeasure`](@ref), e.g. [`Shannon`](@ref), [`Renyi`](@ref) or [`Tsallis`](@ref) entropy, and we let  $Q_q$ be either on the Euclidean, Wooters, Kullback, q-Kullback, Jensen or q-Jensen  distance as

$$
Q_q[P] = Q_q^0\cdot D[P, P_e],
$$

where $D[P, P_e]$ is the distance between the obtained distribution $P$ and a uniform distribution with the same maximum number of bins, measured by the distance measure `dist`.

## Usage

The statistical complexity is exclusively used in combination with the chosen information measure (typically an entropy). The estimated value of the information measure can be accessed as a `Ref` value of the struct as

```julia
x = randn(100)
c = StatisticalComplexity()
compl = complexity(c, x)
entr = first(entropy_complexity(c, x)) # both complexity and entropy value
```

`complexity(c::StatisticalComplexity, x)` returns only the statistical complexity. To obtain both the value of the entropy (or other information measure) and the statistical complexity together as a `Tuple`, use the wrapper [`entropy_complexity`](@ref).

See also: [`entropy_complexity_curves`](@ref).
