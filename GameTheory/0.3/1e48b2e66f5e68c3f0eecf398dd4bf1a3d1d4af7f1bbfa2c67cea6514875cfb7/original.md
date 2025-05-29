```
StochasticFictitiousPlay{N, T, TG, TD}
```

Type representing a stochastic fictitious play model with N players.

# Fields

  * `players::NTuple{N,Player{N,T}}` : Tuple of `Player` instances.
  * `nums_actions::NTuple{N,Int}` : Tuple of the numbers of actions, one for each player.
  * `gain::TG<:AbstractGain` : Gain type.
  * `d::TD<:Distributions.Distribution` : `Distribution` instance from which payoff perturbations are drawn.
