```
solve(gprob::GreekProblem, method::FiniteDifference{S,A}, pricing_method::P) where {S<:FDScheme,P<:AbstractPricingMethod,A}
```

有限差分を使用して一次ギリシャ問題を解決します。

# 引数

  * `gprob`: 解決すべきギリシャ問題。
  * `method`: 有限差分法の設定。
  * `pricing_method`: 価格設定に使用する方法。

# 戻り値

  * 計算されたギリシャを含む `GreekResult`。
