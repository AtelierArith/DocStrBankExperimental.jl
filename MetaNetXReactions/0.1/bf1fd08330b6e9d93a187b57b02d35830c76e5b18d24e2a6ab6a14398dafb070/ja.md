```julia
get_reaction_from_rhea(rid::Int64; should_cache) -> Any

```

Rhea ID `rid` に対応する反応データを取得します。この関数はデフォルトで自動的にキャッシュされます。`should_cache` を使用してこの動作を変更します。
