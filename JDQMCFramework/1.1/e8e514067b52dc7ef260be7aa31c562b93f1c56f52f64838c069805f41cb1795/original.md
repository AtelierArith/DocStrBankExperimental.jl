```
abstract type AbstractChkbrdPropagator{T,E} <: AbstractPropagator{T,E} end
```

Abstract type to represent imaginary time propagator matrices $B$ defined with the exponentiated hopping matrix $K$ represented by the checkerboard approximation.
