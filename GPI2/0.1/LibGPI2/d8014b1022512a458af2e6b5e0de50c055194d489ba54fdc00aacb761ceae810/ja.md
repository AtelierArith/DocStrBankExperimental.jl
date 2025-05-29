```
gaspi_segment_delete(segment_id)
```

指定されたセグメントを削除します。

### パラメータ

  * `segment_id`: 削除するセグメントの識別子。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_segment_delete (const gaspi_segment_id_t segment_id);
```
