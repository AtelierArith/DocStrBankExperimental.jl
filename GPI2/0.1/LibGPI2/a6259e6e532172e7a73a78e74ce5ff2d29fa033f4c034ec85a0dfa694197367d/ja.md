```
gaspi_queue_size(queue, queue_size)
```

指定されたキューの現在の要素数を取得します。

### パラメータ

  * `queue`: サイズを取得するキュー。
  * `queue_size`: キュー内のサイズ/要素を格納する出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_size (const gaspi_queue_id_t queue, gaspi_number_t * const queue_size);
```
