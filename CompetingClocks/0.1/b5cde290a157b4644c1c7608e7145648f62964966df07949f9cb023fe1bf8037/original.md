```
CombinedNextReaction{KeyType,TimeType}()
```

This combines Next Reaction Method and Modified Next Reaction Method. The Next Reaction Method is from Gibson and Bruck in their 2000 paper called ["Efficient Exact Stochastic Simulation of Chemical Systems with Many Species and Many Channels"](https://doi.org/10.1021/jp993732q).  The Modified Next Reaction Method is from David F. Anderson's 2007 paper,  ["A modified Next Reaction Method for simulating chemical systems with time dependent propensities and delays"](https://doi.org/10.1063/1.2799998).  Both methods reuse draws of random numbers. The former works by accumulating  survival of a distribution in a linear space and the latter works by accumulating  survival of a distribution in a log space.

Each enabled clock specifies a univariate distribution from the `Distributions` package. Every distribution is more precise being sampled in the manner of the Next Reaction method (linear space) or the manner of the Modified Next Reaction method (log space). This sampler chooses which space to use depending on the type of the `UnivariateDistribution` and based on performance timings that are done during package testing. Defaults are set for those distributions included in the `Distributions.jl` package. If you want to add a distribution, then define:

```julia
sampling_space(::MyDistribution) = LogSampling
```

If you want to override a choice in the library, then create a sub-type of the given distribution, and specify its sampling space.

```julia
struct LinearGamma <: Distributions.Gamma end
sampling_space(::LinearGamma) = LinearSampling
```

If you want to test a distribution, look at `tests/nrmetric.jl` to see how distributions are timed.
