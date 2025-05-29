```
solve(gprob::SecondOrderGreekProblem, ::AnalyticGreek, ::BlackScholesAnalytic)
```

ブラック-ショールズの閉形式の公式を使用して、二次ギリシャ問題を解決します。

# 引数

  * `gprob`: 解決する二次ギリシャ問題。
  * `::AnalyticGreek`: 使用する方法（解析的公式）。
  * `::BlackScholesAnalytic`: 価格設定方法（ブラック-ショールズ解析）。

# 戻り値

  * 計算された二次ギリシャを含む `GreekResult`。
