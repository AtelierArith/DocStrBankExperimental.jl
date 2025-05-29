```
SymPropagators
```

A union of the all the symmetric propagators types to help test whether a propagator type is symmetric. Assuming `typeof{B} <: AbstractPropagator` returns `true`, if `typeof(B) <: SymPropagators` returns `true`, then `B` represents a symmetric propagator, otherwise it represents an asymmetric propagator.
