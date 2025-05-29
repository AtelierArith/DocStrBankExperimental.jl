```julia
struct Rolling <: BaytesCore.DataStructure
```

サンプラーのデータサイズが時間とともにロールされるかどうかを決定します。

# フィールド

  * `length::Int64`: ローリングウィンドウ。
  * `index::BaytesCore.Iterator`: 最大可視インデックス
