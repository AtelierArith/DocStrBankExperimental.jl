```
solve(gprob::GreekProblem{PricingProblem{VanillaOption{TS,TE,European,B,C},I}, L}, ::AnalyticGreek, ::BlackScholesAnalytic) where {TS,TE,B,C,L, I<:BlackScholesInputs}
```

ヨーロピアン・バニラオプションのための一次ギリシャ問題を、閉じた形式のブラック-ショールズ式を使用して解決します。

# 引数

  * `gprob`: 解決すべきギリシャ問題。
  * `::AnalyticGreek`: 使用する方法（解析式）。
  * `::BlackScholesAnalytic`: 価格設定方法（ブラック-ショールズ解析）。

# 戻り値

  * 計算されたギリシャを含む `GreekResult`。
