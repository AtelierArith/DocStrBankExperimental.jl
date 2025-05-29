```
DimPoints <: AbstractArray

DimPoints(x; order)
DimPoints(dims::Tuple; order)
DimPoints(dims::Dimension; order)
```

`CartesianIndices`のように、次元インデックスの点の値のためのものです。`dims`のルックアップ値のすべての組み合わせに対する`Tuple`ルックアップ値の`Array`として振る舞います（それが何であれ）。

`Dimension`、`Dimension`の`Tuple`、または`dims`メソッドを定義するオブジェクト`x`を渡すことができます。

# キーワード

  * `order`: 点の順序を決定し、デフォルトでは`dims`の順序と同じです。
