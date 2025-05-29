```
gaspi_queue_max(queue_max)
```

使用可能な最大キュー数を取得します。これは、初期化されたキューの最大数と動的に作成されたキューの合計です。

### パラメータ

  * `queue_max`: 最大キュー数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_max(gaspi_number_t * const queue_max);
```
