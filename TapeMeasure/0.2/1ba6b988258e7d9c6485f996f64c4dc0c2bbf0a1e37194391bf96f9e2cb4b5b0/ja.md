```
mutable struct VDimensions{T, S}
```

プロットに表示できるオブジェクトのための適切な次元を表す可変構造体です。Plots.jlまたはMakie.jlを使用します。

# フィールド

  * `xs::Vector{T}`: x座標を含むベクトル。
  * `ys::Vector{S}`: y座標を含むベクトル。
  * `labels::Labels{T, S}`: xおよびy座標のラベルを含む`Labels`のインスタンス。
  * `minor_lines::Vector{T}`: 小さな拡張線の位置を含むベクトル。
  * `major_lines::Vector{T}`: 大きな拡張線の位置を含むベクトル。
  * `offset::T`: 次元のオフセット値を格納します。

# 型パラメータ

  * `T`: `xs`、`minor_lines`、`major_lines`ベクトルおよび`offset`値の要素の型。
  * `S`: `ys`ベクトルの要素の型。
