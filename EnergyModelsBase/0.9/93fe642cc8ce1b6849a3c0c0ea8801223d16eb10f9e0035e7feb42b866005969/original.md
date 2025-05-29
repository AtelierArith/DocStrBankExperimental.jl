```
struct CyclicRepresentative <: Cyclic
```

`StorageBehavior` in which cyclic behaviour is achieved within the lowest time structure excluding operational times.

In the case of `TwoLevel{SimpleTimes}`, this approach is similar to `CyclicStrategic`. In the case of `TwoLevel{RepresentativePeriods{SimpleTimes}}`, this approach differs from `CyclicStrategic` as the cyclic constraint is enforeced within each representative period.
