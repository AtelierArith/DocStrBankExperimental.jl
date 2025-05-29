```
get_matrix(
    daf::DafReader,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [default::Union{StorageReal, StorageMatrix, Nothing, UndefInitializer} = undef,
    relayout::Bool = true]
)::Maybe{NamedMatrix}
```

`daf`の`rows_axis`と`columns_axis`に対して、いくつかの`name`を持つ列優先の行列プロパティを取得します。結果の軸の名前は、関連する軸エントリの名前です（[`axis_vector`](@ref)によって返されるのと同じです）。

`relayout`（デフォルト）を指定した場合、行列が他のメモリレイアウト（つまり、軸が反転した状態）でのみ保存されている場合、自動的に[`relayout!`](@ref)を呼び出して結果を計算します。`daf`が[`DafWriter`](@ref)である場合、結果を将来の使用のために保存します。それ以外の場合は、[`MemoryData`](@ref CacheGroup)としてキャッシュします。これにより非常に大きなメモリがロックされる可能性があります; [`empty_cache!`](@ref)を呼び出して解放できます。

最初に`rows_axis`と`columns_axis`が`daf`に存在することを確認します。`default`が`undef`（デフォルト）の場合、最初に`name`行列が`daf`に存在することを確認します。それ以外の場合、`default`が`nothing`であれば、それが返されます。`default`が`StorageMatrix`である場合、`rows_axis`と`columns_axis`と同じサイズでなければならず、返されます。それ以外の場合、正しいサイズの新しい`Matrix`が作成され、`default`を含んで返されます。
