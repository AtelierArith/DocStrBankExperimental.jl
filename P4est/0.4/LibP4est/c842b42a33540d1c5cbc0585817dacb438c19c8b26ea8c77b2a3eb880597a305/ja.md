```
p8est_connectivity_inflate(buffer)
```

メモリバッファから新しい接続性を作成します。

### パラメータ

  * `buffer`:[in] このメモリバッファから接続性が作成されます。

### 戻り値

新しく作成された接続性、またはエラーの場合はNULL。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_inflate (sc_array_t * buffer);
```
