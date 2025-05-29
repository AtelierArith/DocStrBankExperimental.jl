```julia
struct EinsteinAnd <: FuzzyLogic.AbstractAnd
```

アインシュタインTノルムは、結合を$A ∧ B = \frac{AB}{2 - A - B + AB}$として定義します。
