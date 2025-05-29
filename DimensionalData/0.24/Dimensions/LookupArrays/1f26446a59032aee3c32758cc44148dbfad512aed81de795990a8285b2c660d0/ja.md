```
Metadata <: AbstractMetadata

Metadata{X}(val::Union{Dict,NamedTuple})
Metadata{X}(pairs::Pair...) => Metadata{Dict}
Metadata{X}(; kw...) => Metadata{NamedTuple}
```

一般的な [`Metadata`](@ref) オブジェクトです。`X` 型パラメータは、必要に応じてメソッドディスパッチのためにメタデータを分類します。
