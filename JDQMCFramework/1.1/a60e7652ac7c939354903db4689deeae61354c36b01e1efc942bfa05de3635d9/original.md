```
abstract type AbstractExactPropagator{T,E} <: AbstractPropagator{T,E} end
```

Abstract type to represent imaginary time propagator matrices $B$ defined with an exactly exponentiated hopping matrix $K$.
