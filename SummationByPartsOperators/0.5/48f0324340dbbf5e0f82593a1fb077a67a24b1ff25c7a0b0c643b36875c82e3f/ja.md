```
VariableLinearAdvectionNonperiodicSemidiscretization(D, Di, a, split_form,
                                                     left_bc, right_bc)
```

境界条件 `left_bc(t)`、`right_bc(t)` を持つ線形輸送方程式の半離散化     $\partial_t u(t,x) + \partial_x ( a(x) u(t,x) ) = 0$。

`D` は SBP 微分演算子、`Di` は関連する減衰演算子または `nothing`、`a(x)` は変数係数、`split_form::Union{Val(false), Val(true)}` は標準の分割形式または保存形式を使用するかどうかを決定します。
