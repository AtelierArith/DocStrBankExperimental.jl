```
sc_array_sort(array, compar)
```

配列を比較関数に従って昇順にソートします。

### パラメータ

  * `array`:[in] ソートする配列。
  * `compar`:[in] 使用する比較関数。

### プロトタイプ

```c
void sc_array_sort (sc_array_t * array, int (*compar) (const void *, const void *));
```
