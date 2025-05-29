```
AbstractAlgorithmConstraint
```

A mechanism for constraining which operations can be performed by an algorithm for solving ODEs.

For example, an unconstrained algorithm might compute a Runge-Kutta stage by taking linear combinations of tendencies; i.e., by adding quantities of the form `dt * tendency(state)`. On the other hand, a "strong stability preserving" algorithm can only take linear combinations of "incremented states"; i.e., it only adds quantities of the form `state + dt * coefficient * tendency(state)`.
