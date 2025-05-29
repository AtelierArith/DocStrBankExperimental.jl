```
dissipation_operator([source_of_coefficients=MattssonSvärdNordström2004()],
                     D::DerivativeOperator{T};
                     strength=one(T),
                     order::Int=accuracy_order(D),
                     mode=D.coefficients.mode)
```

Create a negative semidefinite `DissipationOperator` using undivided differences approximating a weighted `order`-th derivative adapted to the derivative operator `D` with coefficients given in `source_of_coefficients`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.
