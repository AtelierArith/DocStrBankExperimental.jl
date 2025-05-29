```
RaggedArray{T,I}
```

値とインデックスからなる「ラグド」配列構造

# フィールド

  * `vals`: 値を含む `Vector{T}`
  * `inds`: インデックスを含む `Vector{I}`

このアプリケーションでは、`RaggedArray` はその `sum!` メソッドでのみ使用されます。
