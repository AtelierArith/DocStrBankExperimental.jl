```
gaspi_segment_list(num, segment_id_list)
```

ローカルに割り当てられたセグメントIDのリストを取得します。

### パラメータ

  * `num`: セグメントの数。
  * `segment_id_list`: 割り当てられたセグメントのIDを含む配列を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_list (const gaspi_number_t num, gaspi_segment_id_t * const segment_id_list);
```
