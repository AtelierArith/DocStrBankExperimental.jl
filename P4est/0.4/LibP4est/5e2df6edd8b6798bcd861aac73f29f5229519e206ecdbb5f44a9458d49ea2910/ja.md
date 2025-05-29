```
sc_array_uniq(array, compar)
```

ソートされた配列から重複エントリを削除します。この関数はビューには使用できません。

### パラメータ

  * `array`:[in,out] 必要に応じて配列のサイズが減少します。
  * `compar`:[in] 使用する比較関数。

### プロトタイプ

```c
void sc_array_uniq (sc_array_t * array, int (*compar) (const void *, const void *));
```
