```julia
struct NilpotentAnd <: FuzzyLogic.AbstractAnd
```

ニルポテントT-ノルムは、$A ∧ B = \min(A, B)$ のように結合を定義します。$A + B > 1$ の場合、$A ∧ B = 0$ それ以外の場合。
