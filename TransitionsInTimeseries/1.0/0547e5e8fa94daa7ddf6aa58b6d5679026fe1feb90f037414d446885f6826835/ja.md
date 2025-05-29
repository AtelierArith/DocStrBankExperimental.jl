```
SegmentedWindowResults <: ChangesResults
```

[`estimate_changes`](@ref)を使用して[`SegmentedWindowConfig`](@ref)と共に使用される出力を含む構造体です。さらなる分析、視覚化、または[`significant_transitions`](@ref)に渡すために使用できます。

ユーザーがアクセスできる以下のフィールドがあります。

  * `x`: 入力時系列。
  * `t`: 入力時系列の時間ベクトル。
  * `x_indicator::Vector{Matrix}`、`x_indicator[k]`は`k`-thセグメントのインジケーター時系列（各列が1つのインジケーターの行列）。
  * `t_indicator::Vector{Vector}`、`t_indicator[k]`は`k`-thセグメントのインジケーター時系列の時間ベクトル。
  * `x_change::Matrix`、`x[k, i]`は`k`-thセグメントの`i`-thインジケーターの変化メトリック値。
  * `t_change`、変化メトリックの時間ベクトル。
  * `config::SegmentedWindowConfig`、分析に使用されたもの。
  * `i1::Vector{Int}` 各セグメントの開始時間に対応するインデックス。
  * `i2::Vector{Int}` 各セグメントの終了時間に対応するインデックス。
  * `precomp_change_metrics` 各セグメントの事前計算された変化メトリックを含むベクトル。
