```
refine(collection::DataCollection, datasets::Vector{DataSet}, ident::Identifier)
```

`datasets`（`collection`から）をフィルタリングして、識別子`ident`に一致するデータセットを取得します。

この関数には、プラグインがさらなるフィルタリングを適用できるアドバイスエントリポイントが含まれており、`refine(::Vector{DataSet}, ::Identifier, ::Vector{String})`メソッドに適用されます。
