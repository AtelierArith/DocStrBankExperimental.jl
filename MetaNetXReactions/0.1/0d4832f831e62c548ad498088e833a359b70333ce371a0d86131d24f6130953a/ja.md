```julia
get_metabolite_from_chebi(cid::Int64; should_cache) -> Any

```

ChEBI id `cid` に対応する代謝物データを取得します。この関数はデフォルトで自動的にキャッシュされます。`should_cache` を使用してこの動作を変更します。
