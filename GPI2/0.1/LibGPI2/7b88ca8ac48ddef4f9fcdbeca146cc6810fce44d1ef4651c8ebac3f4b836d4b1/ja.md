```
gaspi_notify_reset(segment_id_local, notification_id, old_notification_val)
```

指定された通知をリセットし（その値を取得します）。

### パラメータ

  * `segment_id_local`: セグメント識別子。
  * `notification_id`: リセットする通知の識別子。
  * `old_notification_val`: リセット前の通知の値を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_notify_reset (const gaspi_segment_id_t segment_id_local, const gaspi_notification_id_t notification_id, gaspi_notification_t * const old_notification_val);
```
