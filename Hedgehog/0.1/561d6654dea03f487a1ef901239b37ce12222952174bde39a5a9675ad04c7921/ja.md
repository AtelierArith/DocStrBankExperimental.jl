```
solve(prob::PricingProblem{VanillaOption{European}}, ::BlackScholesAnalytic) -> AnalyticSolution
```

ブラック-ショールズモデルの下でヨーロピアンバニラオプションの価格を計算します。

# 引数

  * `prob::PricingProblem`: ペイオフと市場入力を含む価格設定問題。
  * `BlackScholesAnalytic`: 分析的価格設定方法のマーカー。

# 戻り値

  * `AnalyticSolution`: ブラック-ショールズの仮定の下での価格設定された解。

# 注意事項

  * フォワード測定の定式化を使用します。
  * ボラティリティがゼロの場合は内在価値にフォールバックします。
