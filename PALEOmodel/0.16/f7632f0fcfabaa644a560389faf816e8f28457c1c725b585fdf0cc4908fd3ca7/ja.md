```
FieldArray
```

一般的な [xarray](https://xarray.pydata.org/en/stable/index.html) のような、または [IRIS](https://scitools-iris.readthedocs.io/en/latest/) のような n 次元配列で、名前付きの次元とオプションの座標を持っています。

注意: これはシンプルで一般的なものであり、効率的ではありません!!! モデル出力を表現するためのものであり、数値的に集中的な計算には適していません。

# フィールド

  * `name::String`: 変数名
  * `values::AbstractArray`: 値の n 次元配列
  * `dims_coords::Vector{Pair{PALEOboxes.NamedDimension, Vector{PALEOmodel.FieldArray}}}`: オプションの付随座標を持つ次元の名前
  * `attributes::Union{Nothing, Dict{Symbol, Any}}`: 変数の属性
