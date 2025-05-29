```
save_snapshot_in_global_database(trial_id::UUID, state, [label])
```

グローバルデータベースから特定のトライアルの結果を、提供された `state` とオプションの `label` で保存します。ワーカーノードにいる場合はマスターノードにリダイレクトします。アクセスを保護するためにロックします。
