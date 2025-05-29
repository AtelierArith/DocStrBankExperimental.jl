```
CubicPeriodicSemidiscretization(D, Di, split_form)
```

周期境界条件を持つ三次保存法則の半離散化     $\partial_t u(t,x) + \partial_x u(t,x)^3 = 0$。

`D` は一次導関数のSBP演算子であり、`Di` は関連する散逸演算子または `nothing` であり、`split_form::Union{Val(true), Val(false)}` は標準の分割形式または保存形式が使用されるかどうかを決定します。
