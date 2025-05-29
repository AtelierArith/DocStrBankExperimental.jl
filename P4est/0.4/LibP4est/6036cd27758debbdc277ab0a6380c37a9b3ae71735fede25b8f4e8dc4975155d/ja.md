```
sc_array_checksum(array)
```

配列データのadler32チェックサムを計算します（zlibのドキュメントを参照）。これはcrc32よりも高速なチェックサムであり、ゼロをデータとして扱うことができます。

### プロトタイプ

```c
unsigned int sc_array_checksum (sc_array_t * array);
```
