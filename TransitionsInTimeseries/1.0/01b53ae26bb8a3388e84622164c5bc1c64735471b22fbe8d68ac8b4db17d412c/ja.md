```
SlopeChangeResults <: ChangesResults
```

[`estimate_changes`](@ref)を[`SlopeChangeConfig`](@ref)と共に使用した出力を含む構造体です。さらなる分析、視覚化、または[`significant_transitions`](@ref)に渡すために使用できます。[`significant_transitions`](@ref)で使用できる唯一の有意性タイプは[`SlopeChangeSignificance`](@ref)です。

ユーザーがアクセスできる以下のフィールドがあります：

  * `x`: 入力時系列。
  * `t`: 入力時系列の時間ベクトル。
  * `x_indicator`: インジケータ時系列。
  * `t_indicator`: インジケータ時系列の時間ベクトル。
  * `t_change`: 傾きが変化する時間。
  * `fitparams = a, b, c, d`: `t_change`前のフィッティングされた線形係数`a + b*t`と`t_change`後の`c + d*t`。
