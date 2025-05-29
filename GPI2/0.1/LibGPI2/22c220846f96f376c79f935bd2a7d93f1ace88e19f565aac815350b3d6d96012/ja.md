```
gaspi_transfer_size_max(transfer_size_max)
```

単一のリクエスト（読み取り、書き込みなど）で通信できる最大サイズ（バイト単位）を取得します。

### パラメータ

  * `transfer_size_max`: 最大転送サイズを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_transfer_size_max (gaspi_size_t * const transfer_size_max);
```
