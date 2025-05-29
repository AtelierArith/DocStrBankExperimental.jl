```
BackupCallback{backend}(trigger::AbstractCallback, filename; [warn = IOWARN[]])
```

指定された`filename`にシミュレーションの全状態をダンプするコールバックを作成します。

# 拡張ヘルプ

静的パラメータと完全なスナップショットで構成されるシミュレーションの全状態は、`trigger`コールバックがトリガーされるたびに保存されます。データファイルは書き込みの前に切り詰められます。
