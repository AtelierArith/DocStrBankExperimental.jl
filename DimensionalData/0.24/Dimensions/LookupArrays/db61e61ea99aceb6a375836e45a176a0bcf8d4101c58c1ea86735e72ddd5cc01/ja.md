```
NoMetadata <: AbstractMetadata

NoMetadata()
```

オブジェクトにメタデータがないことを示します。しかし、`nothing`を使用するのとは異なり、`get`、`keys`、および`haskey`はそれに対しても機能し、`get`は常にフォールバック引数を返します。`keys`は`()`を返し、`haskey`は常に`false`を返します。
