```
gaspi_notification_num(notification_num)
```

利用可能な通知IDの数を取得します。重要な点は、許可されているIDが [ 0, notification_num ) の範囲内であることです。

### パラメータ

  * `notification_num`: 利用可能な通知IDの数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_notification_num (gaspi_number_t * const notification_num);
```
