```
sc_array_is_sorted(array, compar)
```

配列が比較関数に従ってソートされているかどうかを確認します。

### パラメータ

  * `array`:[in] 確認する配列。
  * `compar`:[in] 使用する比較関数。

### 戻り値

配列がソートされていれば真、そうでなければ偽。

### プロトタイプ

```c
int sc_array_is_sorted (sc_array_t * array, int (*compar) (const void *, const void *));
```
