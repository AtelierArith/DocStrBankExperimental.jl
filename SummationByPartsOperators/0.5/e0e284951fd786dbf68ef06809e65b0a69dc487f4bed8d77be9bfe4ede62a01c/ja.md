```
QuarticNonconvexPeriodicSemidiscretization(D, Di, split_form)
```

周期境界条件を持つ四次非凸保存則の半離散化     $\partial_t u(t,x) + \partial_x ( u(t,x)^4 - 10 u(t,x)^2 + 3 u(t,x) ) = 0$。

`D` は一次導関数のSBP演算子であり、`Di` は関連する散逸演算子または `nothing` であり、`split_form::Union{Val(true), Val(false)}` は標準の分割形式または保存形式が使用されるかどうかを決定します。
