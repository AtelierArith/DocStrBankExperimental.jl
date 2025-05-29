```
extract_results(post_mod::Modification, config, data) -> results
```

[`e4st_post`](@ref) の主なステップの1つです。`data`（E4ST実行からデシリアライズされたデータの完全なセット）から結果を抽出（または新しい結果を計算）します。これにより、`sim_name` を `results` にマッピングする `OrderedDict` に保存されます。次のステップについては [`combine_results`](@ref) を参照してください。

過剰なメモリ使用を防ぐためにこれを行うことに注意してください。大量のシミュレーションで [`e4st_post`](@ref) が実行されると、すべてのシミュレーションの `data` の完全なセットをメモリに保存することは、RAMを過剰に消費する可能性があります。
