```
gaspi_queue_delete(queue)
```

新しい通信キューを削除します。

### パラメータ

  * `queue`: 削除するキューID。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_delete(const gaspi_queue_id_t queue);
```
