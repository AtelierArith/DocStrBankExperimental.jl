```
solve(gprob::SecondOrderGreekProblem, ::ForwardAD, pricing_method::P) where {P<:AbstractPricingMethod}
```

自動微分を使用して二次ギリシャ問題を解決します。

# 引数

  * `gprob`: 解決する二次ギリシャ問題。
  * `::ForwardAD`: 使用する方法（自動微分）。
  * `pricing_method`: 価格設定に使用する方法。

# 戻り値

  * 計算された二次ギリシャを含む `GreekResult`。
