```
gaspi_queue_create(queue, timeout_ms)
```

新しい通信キューを作成します。

### パラメータ

  * `queue`: 作成されたキューのIDを持つ出力パラメータ。
  * `timeout_ms`: ミリ秒単位のタイムアウト値。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_create(gaspi_queue_id_t * const queue, const gaspi_timeout_t timeout_ms);
```
