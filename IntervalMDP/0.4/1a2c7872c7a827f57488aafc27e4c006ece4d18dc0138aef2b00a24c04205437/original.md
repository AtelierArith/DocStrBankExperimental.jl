```
Specification{F <: Property}
```

A specfication is a property together with a satisfaction mode and a strategy mode.  The satisfaction mode is either `Optimistic` or `Pessimistic`. See [`SatisfactionMode`](@ref) for more details. The strategy  mode is either `Maxmize` or `Minimize`. See [`StrategyMode`](@ref) for more details.

### Fields

  * `prop::F`: verification property (either temporal logic or reachability-like).
  * `satisfaction::SatisfactionMode`: satisfaction mode (either optimistic or pessimistic). Default is pessimistic.
  * `strategy::StrategyMode`: strategy mode (either maximize or minimize). Default is maximize.
