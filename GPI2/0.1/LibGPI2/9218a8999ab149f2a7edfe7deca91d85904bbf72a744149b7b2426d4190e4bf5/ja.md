```
gaspi_queue_num(queue_num)
```

通信のために利用可能なキューの数を取得します。

### パラメータ

  * `queue_num`: キューの数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_num (gaspi_number_t * const queue_num);
```
