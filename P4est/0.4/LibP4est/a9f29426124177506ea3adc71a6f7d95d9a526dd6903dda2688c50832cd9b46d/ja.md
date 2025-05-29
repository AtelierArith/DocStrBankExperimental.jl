```
sc_hash_array_lookup(hash_array, v, position)
```

ハッシュ配列にオブジェクトが含まれているか確認します。

### パラメータ

  * `v`:[in] オブジェクトへのポインタ。
  * `position`:[out] position != NULL の場合、*position は見つかった場合に既に含まれているオブジェクトの配列位置に設定されます。

### 戻り値

オブジェクトが見つかった場合は true を返し、そうでない場合は false を返します。

### プロトタイプ

```c
int sc_hash_array_lookup (sc_hash_array_t * hash_array, void *v, size_t *position);
```
