```julia
get_metabolite_from_metanetx(
    id::String;
    should_cache
) -> Any

```

MetaNetX ID `id` に対応する代謝物データを取得します。この関数はデフォルトで自動的にキャッシュされます。`should_cache` を使用してこの動作を変更します。
