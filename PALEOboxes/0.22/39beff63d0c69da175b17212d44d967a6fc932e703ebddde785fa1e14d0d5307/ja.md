```
internal_size(Space::Type{<:AbstractSpace}, mesh::AbstractMesh; [subdomain=""] [space=:cell]) -> NTuple{ndims, Int}
```

モデル変数に使用する配列サイズ。

すべての `AbstractMesh` 具体的なサブタイプ（UnstructuredVectorGrid、CartesianLinearGrid、...）はこのメソッドを実装する必要があります。

# オプションのキーワード引数

  * `subdomain::String=""`: 名前付きサブドメイン
