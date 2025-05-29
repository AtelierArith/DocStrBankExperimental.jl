```
Corpus{T<:NamedTuple,D}
```

コーパスは、いくつかのメタデータとともに[`Document`](@ref)のコレクションです。2つのフィールドがあります。

  * `documents::Vector{Document{D}}`
  * `metadata::T`

`Corpus`内の各`Document`は、同じ型のメタデータを持っている必要があります。
