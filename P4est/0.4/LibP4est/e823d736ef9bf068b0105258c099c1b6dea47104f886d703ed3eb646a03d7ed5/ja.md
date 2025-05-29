```
sc_hash_lookup(hash, v, found)
```

ハッシュテーブルにオブジェクトが含まれているかどうかを確認します。

### パラメータ

  * `v`:[in] ルックアップするオブジェクト。
  * `found`:[out] found != NULL の場合、*found はオブジェクトが見つかった場合に既に含まれているオブジェクトへのポインタのアドレスに設定されます。上書きするには **found に代入できます。

### 戻り値

オブジェクトが見つかった場合は true を返し、そうでない場合は false を返します。

### プロトタイプ

```c
int sc_hash_lookup (sc_hash_t * hash, void *v, void ***found);
```
