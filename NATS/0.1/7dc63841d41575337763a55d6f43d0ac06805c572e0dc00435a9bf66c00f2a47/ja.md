```julia
subscribe(
    f,
    connection,
    subject;
    queue_group,
    spawn,
    channel_size,
    monitoring_throttle_seconds
)

```

サブジェクトにサブスクライブします。

オプションのキーワード引数は次のとおりです：

  * `queue_group`: NATSサーバーはメッセージをキューグループメンバー間で分配します
  * `spawn`: `true`の場合、各`f`呼び出しのためにタスクが生成されます。そうでない場合、メッセージは順次処理されます。デフォルトは`false`です
  * `channel_size`: 処理のためにバッファリングされる最大アイテム数。満杯の場合、メッセージは無視されます。デフォルトは`524288`で、`NATS_SUBSCRIPTION_CHANNEL_SIZE`環境変数でグローバルに設定できます
  * `monitoring_throttle_seconds`: ハンドラエラーがログに報告される秒単位の時間間隔。デフォルトは`5.0`秒で、`NATS_SUBSCRIPTION_ERROR_THROTTLING_SECONDS`環境変数でグローバルに設定できます
