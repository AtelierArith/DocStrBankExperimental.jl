```
sc_array_bsearch(array, key, compar)
```

配列に対して二分探索を実行します。配列はソートされている必要があります。

### パラメータ

  * `array`:[in] 検索するためのソートされた配列。
  * `key`:[in] 検索対象の要素。
  * `compar`:[in] 使用する比較関数。

### 戻り値

見つかったアイテムの配列内のインデックスを返すか、-1を返します。

### プロトタイプ

```c
ssize_t sc_array_bsearch (sc_array_t * array, const void *key, int (*compar) (const void *, const void *));
```
