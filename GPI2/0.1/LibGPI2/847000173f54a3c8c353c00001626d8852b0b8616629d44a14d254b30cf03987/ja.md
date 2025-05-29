```
gaspi_queue_size_max(queue_size_max)
```

キューに投稿できる最大要素数（未処理のリクエスト）を取得します。

### パラメータ

  * `queue_size_max`: キューに投稿できる最大リクエスト数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_queue_size_max (gaspi_number_t * const queue_size_max);
```
