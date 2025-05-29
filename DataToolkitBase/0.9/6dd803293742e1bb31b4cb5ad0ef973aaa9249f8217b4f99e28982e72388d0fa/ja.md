データ仕様TOML形式は、メタデータとAbstractDataTransformerで構成されたDataSetを含むDataCollectionを構築します。

```
DataCollection
├─ DataSet
│  ├─ AbstractDataTransformer
│  └─ AbstractDataTransformer
├─ DataSet
⋮
```

各スコープ内には、特定の予約属性があります。これらは次のキーの下にこのDictにリストされています：

  * `:collection` は `DataCollection` 用
  * `:dataset` は `DataSet` 用
  * `:transformer` は `AbstractDataTransformer` 用
