```
gaspi_passive_transfer_size_min(passive_transfer_size_min)
```

受動的通信で許可される最小サイズ（バイト単位）を取得します。

### パラメータ

  * `passive_transfer_size_min`: 受動的通信のための最小許可サイズ（バイト単位）を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_passive_transfer_size_min (gaspi_size_t * const passive_transfer_size_min);
```
