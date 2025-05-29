```julia
struct SetOfEvents{Tc<:Tuple, Td<:Tuple} <: BifurcationKit.AbstractEvent
```

Multiple events can be chained together to form a `SetOfEvents`. A `SetOfEvents` is constructed by passing to the constructor `ContinuousEvent`, `DiscreteEvent` or other `SetOfEvents` instances:

```
SetOfEvents(cb1, cb2, cb3)
```

# Example

```
 BifurcationKit.SetOfEvents(BK.FoldDetectCB, BK.BifDetectCB)
```

You can pass as many events as you like.

  * `eventC::Tuple`: Continuous event
  * `eventD::Tuple`: Discrete event
