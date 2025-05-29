```julia
struct NilpotentOr <: FuzzyLogic.AbstractOr
```

ニルポテントS-ノルムは、$A ∨ B = \max(A, B)$ で定義され、$A + B < 1$ の場合、$A ∧ B = 1$ それ以外の場合。
