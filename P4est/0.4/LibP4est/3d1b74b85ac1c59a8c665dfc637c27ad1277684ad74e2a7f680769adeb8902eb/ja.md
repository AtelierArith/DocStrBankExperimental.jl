```
sc_hash_array_insert_unique(hash_array, v, position)
```

オブジェクトがすでに含まれていない場合、ハッシュ配列にオブジェクトを挿入します。オブジェクトは配列にコピーされません。そのために戻り値を使用します。新しいオブジェクトは配列の末尾に追加されることが保証されています。

### パラメータ

  * `v`:[in] オブジェクトへのポインタ。検索のみに使用されます。
  * `position`:[out] position != NULL の場合、*position はすでに含まれているオブジェクトの配列位置に設定されます。存在しない場合は、新しいオブジェクトの位置になります。

### 戻り値

オブジェクトがすでに含まれている場合は NULL を返します。それ以外の場合は、配列内の新しいアドレスを返します。

### プロトタイプ

```c
void *sc_hash_array_insert_unique (sc_hash_array_t * hash_array, void *v, size_t *position);
```
