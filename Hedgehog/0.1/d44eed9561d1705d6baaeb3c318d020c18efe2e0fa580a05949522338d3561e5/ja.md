```
solve(gprob::GreekProblem, ::ForwardAD, pricing_method::P) where {P<:AbstractPricingMethod}
```

自動微分を使用して一次のギリシャ問題を解決します。

# 引数

  * `gprob`: 解決するギリシャ問題。
  * `::ForwardAD`: 使用する方法（自動微分）。
  * `pricing_method`: 価格設定に使用する方法。

# 戻り値

  * 計算されたギリシャを含む名前付きタプル。
