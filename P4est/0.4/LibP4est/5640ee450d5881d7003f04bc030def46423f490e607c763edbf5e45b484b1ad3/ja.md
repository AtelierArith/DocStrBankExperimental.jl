```
sc_hash_memory_used(hash)
```

ハッシュテーブルによって使用されるメモリを計算します。

### パラメータ

  * `hash`:[in] ハッシュテーブル。

### 戻り値

バイト単位で使用されるメモリ。

### プロトタイプ

```c
size_t sc_hash_memory_used (sc_hash_t * hash);
```
