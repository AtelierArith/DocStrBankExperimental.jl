```
struct IrregularGrid{N,B,R,S,T} <: AbstractGrid{N,B,T}
```

パラメータの不規則グリッドの構造体。

# フィールド

  * `lower_bounds::B`: 各パラメータの下限。
  * `upper_bounds::B`: 各パラメータの上限。
  * `grid::G`: パラメータ値のセット。例えば、各列がパラメータベクトルである行列。

# コンストラクタ

`IrregularGrid(lower_bounds, upper_bounds, grid)`を使用して`IrregularGrid`を構築できます。
