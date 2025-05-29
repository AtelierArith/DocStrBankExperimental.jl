```
gaspi_segment_max(segment_max)
```

許可される最大セグメント数を取得します。

### パラメータ

  * `segment_max`: 最大セグメント数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_max (gaspi_number_t * const segment_max);
```
