```
FunctionField(func::F, grid::StructuredGrid{N}, loc; discrete=false, parameters=nothing) where {F,N}
```

指定された関数 `func` を使用して、与えられた `grid` 上に `FunctionField` を作成します。

## 引数:

  * `func::F`: フィールド値を生成するために使用される関数。
  * `grid::StructuredGrid{N}`: 計算領域を定義する構造化グリッド。
  * `loc`: 関数フィールドが定義されるグリッド上のノード位置。
  * `discrete=false`: フィールドが離散的であるべきかどうかを示すフラグ。デフォルトは `false`。
  * `parameters=nothing`: 関数によって使用される追加のパラメータ。デフォルトは `nothing`。
