```julia
struct LukasiewiczAnd <: FuzzyLogic.AbstractAnd
```

ルカシェビッチT-ノルムは、結合を $A ∧ B = \max(0, A + B - 1)$ と定義します。
