```
StochasticFictitiousPlay(g, d[, gain=DecreasingGain()])
```

Construct a `StochasticFictitiousPlay` instance.

# Arguments

  * `g::NormalFormGame` : `NormalFormGame` instance.
  * `d::Distributions.Distribution` : `Distribution` instance from which payoff perturbations are drawn.
  * `gain::AbstractGain` : Argument to specify the gain or step size; `DecreasingGain()` or `ConstantGain(size)`.

# Returns

  * `::StochasticFictitiousPlay` : The stochastic fictitious play model.
