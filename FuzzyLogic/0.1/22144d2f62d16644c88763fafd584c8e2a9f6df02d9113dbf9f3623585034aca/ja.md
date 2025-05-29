```julia
struct BoundedSumOr <: FuzzyLogic.AbstractOr
```

境界和S-ノルムは、論理和を $A ∨ B = \min(1, A + B)$ と定義します。
