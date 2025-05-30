```
SegmentedWindowResults <: ChangesResults
```

[`estimate_changes`](@ref) と [`SegmentedWindowConfig`](@ref) を使用して得られた出力を含む構造体です。さらなる分析、視覚化、または [`significant_transitions`](@ref) に渡すために使用できます。

ユーザーがアクセスできる以下のフィールドがあります。

  * `x`: 入力時系列。
  * `t`: 入力時系列の時間ベクトル。
  * `x_indicator::Vector{Matrix}`、`x_indicator[k]` は `k` 番目のセグメントのインジケーター時系列（各列が1つのインジケーターの行列）です。
  * `t_indicator::Vector{Vector}`、`t_indicator[k]` は `k` 番目のセグメントのインジケーター時系列の時間ベクトルです。
  * `x_change::Matrix`、`x[k, i]` は `k` 番目のセグメントの `i` 番目のインジケーターの変化メトリックです。
  * `t_change`、変化メトリックの時間ベクトル。
  * `config::SegmentedWindowConfig`、分析に使用されたもの。
  * `i1::Vector{Int}` 各セグメントの開始時間に対応するインデックス。
  * `i2::Vector{Int}` 各セグメントの終了時間に対応するインデックス。
  * `precomp_change_metrics` 各セグメントの事前計算された変化メトリックを含むベクトル。
