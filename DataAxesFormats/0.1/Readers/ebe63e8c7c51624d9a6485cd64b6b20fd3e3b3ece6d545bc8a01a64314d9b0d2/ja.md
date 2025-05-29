```
get_vector(
    daf::DafReader,
    axis::AbstractString,
    name::AbstractString;
    [default::Union{StorageScalar, StorageVector, Nothing, UndefInitializer} = undef]
)::Maybe{NamedVector}
```

`daf`の`axis`に対して、`name`のいくつかのベクトルプロパティを取得します。結果の名前はベクトルエントリの名前であり（[`axis_vector`](@ref)によって返されるものと同じ）、特別なプロパティ`name`は、エントリの名前（読み取り専用）を値として持つ配列を返します。

最初に`axis`が`daf`に存在することを確認します。`default`が`undef`（デフォルト）である場合、最初に`name`ベクトルが`daf`に存在することを確認します。それ以外の場合、`default`が`nothing`であれば、それが返されます。もしそれが[`StorageVector`](@ref)であれば、`axis`と同じサイズでなければならず、返されます。もしそれが[`StorageScalar`](@ref)であれば、そうでなければ、正しいサイズの新しい`Vector`が`default`を含むように作成され、返されます。
