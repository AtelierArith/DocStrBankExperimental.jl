```
sc_hash_destroy_null(phash)
```

ハッシュテーブルを破棄し、そのポインタをNULLに設定します。破壊はsc*hash*destroyを使用して行われます。

### パラメータ

  * `phash`:[in,out] ハッシュテーブルへのポインタのアドレス。出力時にポインタはNULLにされます。

### プロトタイプ

```c
void sc_hash_destroy_null (sc_hash_t ** phash);
```
