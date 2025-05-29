```
gaspi_segment_num(segment_num)
```

割り当てられたセグメントの数を取得します。

### パラメータ

  * `segment_num`: 割り当てられたセグメントの数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_num (gaspi_number_t * const segment_num);
```
