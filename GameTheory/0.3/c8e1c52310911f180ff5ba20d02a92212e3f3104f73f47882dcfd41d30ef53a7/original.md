```
StochasticFictitiousPlay(fp[, d=fp.d, gain=fp.gain])
```

Construct a new `StochasticFictitiousPlay` instance from `fp`.

# Arguments

  * `fp::AbstractFictitiousPlay` : `AbstractFictitiousPlay` instance.
  * `d::Distributions.Distribution` : `Distribution` instance from which payoff perturbations are drawn.
  * `gain::AbstractGain` : Argument to specify the gain or step size.

# Returns

  * `::StochasticFictitiousPlay` : The stochastic fictitious play model.
