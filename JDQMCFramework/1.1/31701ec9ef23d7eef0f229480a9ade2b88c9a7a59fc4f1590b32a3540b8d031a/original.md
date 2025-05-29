```
abstract type AbstractPropagator{T<:Continuous, E<:Continuous} end
```

Abstract type to represent imaginary time propagator matrices $B$. All specific propagators types inherit from this abstract type. In the above `T` is data type of the matrix elements of the exponentiated kintetic energy matrix $e^{-\Delta\tau K_l}$ appearing in $B_l$, and `E` is data type of the matrix elements appearing in the diagonal exponentiated potential energy matrix $e^{-\Delta\tau V_l}$.
