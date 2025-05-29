```
sc_array_destroy_null(parray)
```

配列構造体を破壊し、ポインタをNULLに設定します。

### パラメータ

  * `parray`:[in,out] 破壊される配列のアドレスへのポインタ。出力時、*parrayはNULLです。

### プロトタイプ

```c
void sc_array_destroy_null (sc_array_t ** parray);
```
