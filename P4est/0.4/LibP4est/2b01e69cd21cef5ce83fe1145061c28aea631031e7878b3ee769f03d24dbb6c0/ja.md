```
sc_hash_destroy(hash)
```

ハッシュテーブルを破棄します。

アロケータが所有されている場合、これはO(1)で実行されます。そうでない場合はO(N)で実行されます。

!!! note
    [`sc_hash_new`](@ref)でアロケータが提供されている場合、それは破棄されません。


### プロトタイプ

```c
void sc_hash_destroy (sc_hash_t * hash);
```
