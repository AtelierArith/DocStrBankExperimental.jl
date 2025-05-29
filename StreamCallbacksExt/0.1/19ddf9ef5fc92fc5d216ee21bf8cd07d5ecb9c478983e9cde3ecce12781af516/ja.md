```
RunInfo(; creation_time=time(), inference_start=nothing, last_message_time=nothing, stop_sequence=nothing)
```

ストリーミングプロセス中の実行統計とメタデータを追跡します。

# フィールド

  * `creation_time`: コールバックが作成された時刻
  * `inference_start`: モデルが処理を開始した時刻
  * `last_message_time`: 最後に受信したメッセージのタイムスタンプ
  * `stop_sequence`: 生成を停止させたシーケンス（ある場合）
