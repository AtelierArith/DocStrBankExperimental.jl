```
p8est_connectivity_source(source)
```

ソースオブジェクトから接続性を読み取ります。

### パラメータ

  * `source`:[in,out] このソースから接続性が読み取られます。

### 戻り値

新しく作成された接続性、またはエラー時にNULL。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_source (sc_io_source_t * source);
```
