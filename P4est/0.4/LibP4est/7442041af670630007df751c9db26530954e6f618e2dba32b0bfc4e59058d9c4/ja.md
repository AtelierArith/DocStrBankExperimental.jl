```
sc_hash_remove(hash, v, found)
```

ハッシュテーブルからオブジェクトを削除します。

### パラメータ

  * `v`:[in] 削除するオブジェクト。
  * `found`:[out] found != NULL の場合、*found は存在する場合に削除されたオブジェクトに設定されます。

### 戻り値

オブジェクトが見つかった場合は true を返し、含まれていない場合は false を返します。

### プロトタイプ

```c
int sc_hash_remove (sc_hash_t * hash, void *v, void **found);
```
