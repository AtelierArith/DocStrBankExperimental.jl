```
sc_hash_foreach(hash, fn)
```

ハッシュテーブルのすべてのメンバーに対してコールバックを呼び出します。関数 hash*fn と equal*fn はこの関数によって呼び出されません。

### プロトタイプ

```c
void sc_hash_foreach (sc_hash_t * hash, sc_hash_foreach_t fn);
```
