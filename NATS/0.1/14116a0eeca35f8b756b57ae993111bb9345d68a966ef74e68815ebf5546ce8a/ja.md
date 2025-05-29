```julia
subscribe(
    connection,
    subject;
    queue_group,
    channel_size,
    monitoring_throttle_seconds
)

```

同期モードでサブジェクトにサブスクライブします。クライアントは手動で `next` を呼び出してメッセージを取得する必要があります。

オプションのキーワード引数は次のとおりです：

  * `queue_group`: NATSサーバーはメッセージをキューグループメンバー間で分配します
  * `channel_size`: 処理のためにバッファリングされる最大アイテム数。満杯の場合、メッセージは無視されます。デフォルトは `524288` で、`NATS_SUBSCRIPTION_CHANNEL_SIZE` 環境変数でグローバルに設定できます
  * `monitoring_throttle_seconds`: ハンドラーエラーがログに報告される時間間隔（秒単位）。デフォルトは `5.0` 秒で、`NATS_SUBSCRIPTION_ERROR_THROTTLING_SECONDS` 環境変数でグローバルに設定できます
