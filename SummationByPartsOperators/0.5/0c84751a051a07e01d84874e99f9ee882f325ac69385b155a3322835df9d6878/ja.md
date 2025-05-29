```
CubicNonperiodicSemidiscretization(D, Di, split_form, left_bc, right_bc)
```

非周期境界条件 `left_bc(t)`、`right_bc(t)` を持つ立方体保存則の半離散化     $\partial_t u(t,x) + \partial_x u(t,x)^3 = 0$。

`D` は一次導関数のSBP演算子、`Di` は関連する散逸演算子または `nothing` であり、`split_form::Union{Val(true), Val(false)}` は標準の分割形式または保存形式が使用されるかどうかを決定します。
