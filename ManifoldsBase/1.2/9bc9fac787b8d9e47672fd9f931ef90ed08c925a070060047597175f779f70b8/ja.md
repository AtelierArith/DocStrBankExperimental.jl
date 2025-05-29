```
get_basis(M::AbstractManifold, p, B::AbstractBasis; kwargs...) -> CachedBasis
```

多様体 `M` の点 `p` における接空間の基底ベクトルを計算します。

返されるオブジェクトは [`AbstractBasis`](@ref) から派生し、接ベクトルを格納するフィールド `.vectors` を持つ場合があります。または、接ベクトルを暗黙的に格納する場合もあり、その場合は基底ベクトルを取得するために関数 [`get_vectors`](@ref) を使用する必要があります。

関連情報: [`get_coordinates`](@ref), [`get_vector`](@ref)
