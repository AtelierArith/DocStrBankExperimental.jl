```julia
struct PairOfEvents{Tc<:BifurcationKit.AbstractContinuousEvent, Td<:BifurcationKit.AbstractDiscreteEvent} <: BifurcationKit.AbstractEvent
```

Structure to pass a PairOfEvents function to the continuation algorithm. It is composed of a pair ContinuousEvent / DiscreteEvent. A `PairOfEvents` is constructed by passing to the constructor a `ContinuousEvent` and a `DiscreteEvent`:

```
PairOfEvents(contEvent, discreteEvent)
```

## Fields

  * `eventC::BifurcationKit.AbstractContinuousEvent`: Continuous event
  * `eventD::BifurcationKit.AbstractDiscreteEvent`: Discrete event
