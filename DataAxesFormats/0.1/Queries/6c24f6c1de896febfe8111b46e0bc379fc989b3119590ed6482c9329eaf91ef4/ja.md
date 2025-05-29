```
get_query(
    daf::DafReader,
    query::QueryString;
    [cache::Bool = true]
)::Union{StorageScalar, NamedVector, NamedMatrix}
```

`Daf`データに対して完全な`query`を適用し、結果を返します。デフォルトでは、結果をキャッシュするため、繰り返しのクエリが加速されます。これにより、大量のメモリを消費する可能性があります。`cache = false`を指定することで無効にするか、[`empty_cache!`](@ref)を使用してキャッシュされたデータを解放できます。

ショートハンド構文として、`getindex`を使用してこれを呼び出すこともできます。つまり、`[]`演算子を使用します（例：`daf[q"/ cell"]`は`get_query(daf, q"/ cell")`と同等です）。
