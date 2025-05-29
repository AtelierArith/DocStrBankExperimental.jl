```
cartesian_size(Space::Type{<:AbstractSpace}, mesh::AbstractMesh) -> NTuple{ndims, Int}
```

オプション（通常の直交格子のみがこのメソッドを実装する必要があります）：直交ドメインの配列サイズ。

注：これは、`mesh` が内部モデル変数のためにベクトルへのマッピングを実装している場合、`internal_size` とは異なる場合があります。
