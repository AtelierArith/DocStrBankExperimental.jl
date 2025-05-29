```
SteepestDirectionUpdateRule <: DirectionUpdateRule
```

最も単純な更新ルールは、最後の方向の影響を持たず、したがってすべての [`ConjugateGradientDescentState`](@ref)`cgds` に対して更新 $β = 0$ を返すことです。

また、[`conjugate_gradient_descent`](@ref) も参照してください。
