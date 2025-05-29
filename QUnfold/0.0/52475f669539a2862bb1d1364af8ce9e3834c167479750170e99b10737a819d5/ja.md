```
ACC(classifier; kwargs...)
```

調整された分類とカウントのメソッドで、明確な分類器の予測を用いて最小二乗目的を解決します。

正則化強度 `τ > 0` は、Bunse et al. (2022) によって提案された順序量化のための o-ACC メソッドを生み出します: *Ordinal Quantification through Regularization*。

**キーワード引数**

  * `strategy = :softmax` は解法戦略です（下記参照）。
  * `τ = 0.0` は o-ACC のための正則化強度です。
  * `a = Float64[]` は展開分析のための受け入れ因子です。
  * `fit_classifier = true` は与えられた `classifier` をフィットさせるかどうかです。

**戦略**

二項分類の場合、ACC は Forman (2008) によって提案されました: *Quantifying counts and costs via classification*。多クラス設定では、複数の拡張が利用可能です。

  * `:softmax`（デフォルト; 我々のメソッド）は、技術的な正則化項を導入する代わりに、1つの潜在パラメータをゼロに設定することで `:softmax_full_reg` を改善します。
  * `:constrained` は、Hopkins & King (2010) によって提案されたように、最適化を適切な確率密度に制約します: *A method of automated nonparametric content analysis for social science*。
  * `:pinv` は、Bunse (2022) によって議論されたように、最小ノルム制約に類似した擬似逆行列を計算します: *On Multi-Class Extensions of Adjusted Classify and Count*。
  * `:inv` は、Vucetic & Obradovic (2001) によって提案されたように、転送行列 `M` の真の逆行列（存在する場合）を計算します: *Classification on data with biased class distribution*。
  * `:ovr` は、Forman (2008) によって提案されたように、複数の二項一対残りの調整を解決します。
  * `:none` は、調整なしで `CC` メソッドを提供します。
  * `:softmax_full_reg`（我々のメソッド）は、制約を無効にするソフトマックス層を導入します。この戦略は、Bunse (2022) によって提案されたように、技術的な正則化項を使用します: *On Multi-Class Extensions of Adjusted Classify and Count*。
  * `:softmax_reg`（我々のメソッド）は、技術的な正則化項を導入するのに加えて、1つの潜在パラメータをゼロに設定する `:softmax` の変種です。
