```
pgaspi_queue_purge(queue, timeout_ms)
```

キューを消去します。

### パラメータ

  * `queue`: 消去するキュー。
  * `timeout_ms`: 操作のタイムアウト。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR、時間切れの場合はGASPI_TIMEOUTを返します。

### プロトタイプ

```c
gaspi_return_t pgaspi_queue_purge(const gaspi_queue_id_t queue, const gaspi_timeout_t timeout_ms);
```
