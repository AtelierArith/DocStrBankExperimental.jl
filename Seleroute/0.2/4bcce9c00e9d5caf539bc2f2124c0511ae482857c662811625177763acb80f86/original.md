The way uncertainty is implemented. These values are natively supported:

  * `NoUncertaintyHandling`: the uncertainty is not taken into account, only nominal values are used
  * `StochasticUncertainty`: the uncertainty is implemented through stochastic optimisation, i.e. with several (potentially weighted) values of the unknown parameters
  * `RobustUncertainty`: the uncertainty is implemented through robust optimisation, i.e. the unknown parameters belong to a given (bounded) uncertainty set
  * `ObliviousUncertainty`: the uncertainty is implemented through oblivious optimisation, i.e. the unknown parameters belong to an unbouded uncertainty set
