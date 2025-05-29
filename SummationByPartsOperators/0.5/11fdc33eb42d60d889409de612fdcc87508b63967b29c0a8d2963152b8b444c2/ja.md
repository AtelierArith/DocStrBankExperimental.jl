```
BurgersNonperiodicSemidiscretization(D, Di, split_form, left_bc, right_bc)
```

バージャーズ方程式の半離散化     $\partial_t u(t,x) + \partial_x \frac{u(t,x)^2}{2} = 0$ で、境界条件は `left_bc(t)`, `right_bc(t)` です。

`D` は一次導関数のSBP演算子で、`Di` は関連する散逸演算子または `nothing` であり、`split_form::Union{Val(true), Val(false)}` は標準の分割形式または保存形式が使用されるかどうかを決定します。
