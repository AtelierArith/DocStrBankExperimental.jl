```
gaspi_numa_socket(socket)
```

NUMAソケットを取得

### パラメータ

  * `socket`: ソケットを持つ出力パラメータ

### 戻り値

成功した場合はGASPI*SUCCESS、NUMAが有効にされていない状態でGPI2が開始された場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_numa_socket(gaspi_uchar * const socket);
```
