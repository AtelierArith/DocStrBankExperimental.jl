```
mutable struct HDimensions{T, S}
```

プロットに表示できるオブジェクトの水平方向の寸法を表す可変構造体です。Plots.jlまたはMakie.jlを使用します。

# フィールド

  * `xs::Vector{T}`: x座標を含むベクトル。
  * `ys::Vector{S}`: y座標を含むベクトル。
  * `labels::Labels{T, S}`: xおよびy座標のラベルを含む`Labels`のインスタンス。
  * `minor_lines::Vector{S}`: 小グリッド線の位置を含むベクトル。
  * `major_lines::Vector{S}`: 大グリッド線の位置を含むベクトル。
  * `offset::T`: 寸法のオフセット値を格納します。

# 型パラメータ

  * `T`: `xs`ベクトルの要素の型。
  * `S`: `ys`、`minor_lines`、`major_lines`ベクトルおよび`offset`値の要素の型。
