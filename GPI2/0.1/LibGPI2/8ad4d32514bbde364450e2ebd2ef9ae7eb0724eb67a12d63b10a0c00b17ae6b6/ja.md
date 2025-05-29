```
gaspi_transfer_size_min(transfer_size_min)
```

単一のリクエスト（書き込み、読み取りなど）で通信できる最小サイズ（バイト単位）を取得します。

### パラメータ

  * `transfer_size_min`: 転送可能な最小サイズを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_transfer_size_min (gaspi_size_t * const transfer_size_min);
```
