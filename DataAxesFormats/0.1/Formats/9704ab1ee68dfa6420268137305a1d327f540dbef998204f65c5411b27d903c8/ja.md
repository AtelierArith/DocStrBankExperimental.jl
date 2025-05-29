```
empty_cache!(
    daf::DafReader;
    [clear::Maybe{CacheGroup} = nothing,
    keep::Maybe{CacheGroup} = nothing]
)::Nothing
```

キャッシュされたデータをクリアします。デフォルトでは、キャッシュを完全に空にします。特定の [`CacheGroup`](@ref)（例えば、`QueryData` のみをクリアするため）を忘れるために `clear` を指定するか、特定の [`CacheGroup`](@ref)（例えば、`MappedData` のみを保持するため）を除いてすべてを忘れるために `keep` を指定できます。`clear` と `keep` の両方を指定することはできません。

!!! note
    遅いキャッシュ更新操作（行列の再配置、クエリなど）が進行中の場合、キャッシュが一貫した状態になるように、それらが完了するまで待機します。

