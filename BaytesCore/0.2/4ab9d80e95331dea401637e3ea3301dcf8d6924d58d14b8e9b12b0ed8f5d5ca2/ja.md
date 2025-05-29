```julia
struct Expanding <: BaytesCore.DataStructure
```

サンプラーのデータサイズが時間とともに増加しているかどうかを判断します。

# フィールド

  * `index::BaytesCore.Iterator`: 最大可視インデックス
