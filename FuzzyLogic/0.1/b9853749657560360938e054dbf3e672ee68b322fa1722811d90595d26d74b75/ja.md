```julia
struct HamacherOr <: FuzzyLogic.AbstractOr
```

ハマッハーS-ノルムは、$A ∨ B = \frac{A + B - AB}{1 - AB}$（$A \neq 1 \neq B$の場合）として結合を定義し、そうでない場合は$A ∨ B = 1$です。
