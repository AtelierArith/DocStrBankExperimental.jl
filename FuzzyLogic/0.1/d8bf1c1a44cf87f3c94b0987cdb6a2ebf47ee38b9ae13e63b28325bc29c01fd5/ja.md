```julia
struct DrasticAnd <: FuzzyLogic.AbstractAnd
```

ドラステックTノルムは、結合を$A ∧ B = \min(A, B)$として定義し、$A = 1$または$B = 1$の場合は$A ∧ B = 1$、それ以外の場合は$A ∧ B = 0$です。
