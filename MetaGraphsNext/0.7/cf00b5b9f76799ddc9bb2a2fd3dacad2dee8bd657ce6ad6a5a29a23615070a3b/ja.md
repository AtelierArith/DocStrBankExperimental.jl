```
struct DOTFormat <: AbstractGraphFormat end
```

すべてのメタデータタイプが `pairs` をサポートするか、`Nothing` である場合、`MetaGraph` を `DOTFormat` に保存できます。
