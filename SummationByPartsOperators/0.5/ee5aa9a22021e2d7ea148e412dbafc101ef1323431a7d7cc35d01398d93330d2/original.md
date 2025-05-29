```
dissipation_operator(D::PeriodicDerivativeOperator;
                     strength=one(eltype(D)),
                     order=accuracy_order(D),
                     mode=D.coefficients.mode)
```

Create a negative semidefinite `DissipationOperator` using undivided differences approximating a `order`-th derivative with strength `strength` adapted to the derivative operator `D`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
