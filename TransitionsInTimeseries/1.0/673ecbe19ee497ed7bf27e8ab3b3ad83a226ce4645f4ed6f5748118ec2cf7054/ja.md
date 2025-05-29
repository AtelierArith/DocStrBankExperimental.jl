```
SlidingWindowResults <: ChangesResults
```

[`estimate_changes`](@ref)を[`SlidingWindowConfig`](@ref)と共に使用した際の出力を含む構造体です。さらなる分析、視覚化、または[`significant_transitions`](@ref)に渡すために使用できます。

ユーザーがアクセスできる以下のフィールドがあります。

  * `x`: 入力時系列。
  * `t`: 入力時系列の時間ベクトル。
  * `x_indicator`: インジケータ時系列（各列が1つのインジケータの行列）。
  * `t_indicator`: インジケータ時系列の時間ベクトル。
  * `x_change`: 変化メトリック時系列（各列が1つの変化メトリックの行列）。
  * `t_change`: 変化メトリック時系列の時間ベクトル。
  * `config::SlidingWindowConfig`: 分析に使用された設定。
