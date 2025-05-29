```
TensorField(backend::Backend, grid::StructuredGrid{2}, args...; kwargs...)
```

指定された `backend` を使用して、与えられた `grid` 上に名前付きタプルの形で2Dテンソルフィールドを作成します。各コンポーネント `xx`、`yy`、および `xy` は `Field` です。

## 引数:

  * `backend::Backend`: 計算に使用されるバックエンド。
  * `grid::StructuredGrid{2}`: 計算領域を定義する2D構造化グリッド。
  * `args...`: `Field` コンストラクタに渡す追加の位置引数。
  * `kwargs...`: `Field` コンストラクタに渡す追加のキーワード引数。
