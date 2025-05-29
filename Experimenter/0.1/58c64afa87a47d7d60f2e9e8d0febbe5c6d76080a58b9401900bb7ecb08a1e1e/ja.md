```
get_results_from_trial_global_database(trial_id::UUID)
```

特定のトライアルの結果をグローバルデータベースから取得します。ワーカーノードにいる場合はマスターノードにリダイレクトします。アクセスを保護するためにロックします。
