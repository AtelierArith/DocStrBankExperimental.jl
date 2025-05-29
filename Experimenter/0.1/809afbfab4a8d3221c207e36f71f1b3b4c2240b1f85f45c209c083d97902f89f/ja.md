```
get_latest_snapshot_from_global_database(trial_id::UUID)
```

`get_latest_snapshot`と同様ですが、指定されたグローバルデータベースで動作します。分散ノード上にいる場合はマスターワーカーにリダイレクトされます。`@execute`を使用しているときのみ機能します。
