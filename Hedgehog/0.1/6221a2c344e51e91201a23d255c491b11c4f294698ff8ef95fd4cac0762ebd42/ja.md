```
solve(gprob::BatchGreekProblem{P,L}, method::GreekMethod, pricing_method::AbstractPricingMethod) where {P,L}
```

複数のギリシャ問題を同時に解決します。

# 引数

  * `gprob`: 解決するバッチギリシャ問題。
  * `method`: ギリシャ計算に使用する方法。
  * `pricing_method`: 価格設定に使用する方法。

# 戻り値

  * レンズを対応するギリシャにマッピングする辞書。
