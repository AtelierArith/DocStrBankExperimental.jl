```
LNS{TMethodSelector <: MethodSelector, TSolution <: Solution}
```

基本的な大規模近隣探索。

属性

  * `solution`: 現在の解
  * `scheduler`: `Scheduler`
  * `meths_ch`: 構築ヒューリスティック手法のリスト
  * `meths_de`: 破壊手法のリスト
  * `meths_re`: 修復手法のリスト
  * `meths_compat`: どの破壊手法がどの修復手法と併用できるかを示すブール行列。すなわち、`meths_compat[i,j]==true` は、i 番目の破壊手法が j 番目の修復手法と併用できることを示す
  * `temperature`: メトロポリス基準のための温度
  * `params`: LNSParameters、デフォルトではグローバル設定から採用される
