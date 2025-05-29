```julia
two_sided_pvalues(ubc; ess_correction)

```

バイナリカウントのための両側p値を計算します。

連続性補正を伴う正規近似を使用します。

`ess_correction = true`（デフォルト）の場合、標準偏差は効果的サンプルサイズを使用して計算されます。
