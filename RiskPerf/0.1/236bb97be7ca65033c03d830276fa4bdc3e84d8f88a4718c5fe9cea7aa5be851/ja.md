```
upside_potential_ratio(returns, threshold; method=:partial)
```

アップサイドポテンシャル比率は、シャープ比率やソルティーノ比率と同様のリスク調整パフォーマンス指標です。この比率は、分子にアップサイドリターン（`threshold`を超える）だけを考慮し、分母にはダウンサイドリターン（`threshold`未満）だけを考慮します（`downside_deviation`を参照）。

# 引数

  * `returns`:     資産リターンのベクトル。
  * `threshold`:   スカラー値または閾値リターンを示すベクトル。
  * `method`:      `:full`（デフォルト）または`:partial`のいずれか。分母にすべてのリターンの数（`:full`）を使用するか、閾値を超えるリターンの数（`:partial`）のみを使用するかを示します。

# 出典

  * Plantinga, A., van der Meer, R. and Sortino, F. (2001). The Impact of Downside Risk on Risk-Adjusted Performance of Mutual Funds in the Euronext Markets.
