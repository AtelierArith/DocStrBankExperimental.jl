```
sc_hash_insert_unique(hash, v, found)
```

オブジェクトがすでに含まれていない場合、ハッシュテーブルに挿入します。

### パラメータ

  * `v`:[in] 挿入されるオブジェクト。
  * `found`:[out] found != NULL の場合、*found はすでに含まれているポインタのアドレス、または存在しない場合は新しいオブジェクトのアドレスに設定されます。**found に代入して上書きすることができます。

### 戻り値

オブジェクトが追加された場合は true を返し、すでに含まれている場合は false を返します。

### プロトタイプ

```c
int sc_hash_insert_unique (sc_hash_t * hash, void *v, void ***found);
```
