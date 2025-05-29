```julia
struct HamacherAnd <: FuzzyLogic.AbstractAnd
```

ハマッハーT-ノルムは、$A ∧ B = \frac{AB}{A + B - AB}$（$A \neq 0 \neq B$の場合）として結合を定義し、そうでない場合は$A ∧ B = 0$とします。
