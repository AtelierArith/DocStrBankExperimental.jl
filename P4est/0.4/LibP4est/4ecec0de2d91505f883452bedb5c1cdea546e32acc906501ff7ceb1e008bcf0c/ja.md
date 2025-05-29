```
sc_hash_truncate(hash)
```

ハッシュテーブルからすべてのエントリをO(N)で削除します。

アロケータが所有されている場合、[`sc_hash_unlink`](@ref)および[`sc_mempool_truncate`](@ref)を呼び出します。そうでない場合は、すべてのハッシュスロットで[`sc_list_reset`](@ref)を呼び出しますが、これは遅くなります。

### プロトタイプ

```c
void sc_hash_truncate (sc_hash_t * hash);
```
