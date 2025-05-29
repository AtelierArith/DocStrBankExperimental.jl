```
lock_read(rwlock)
lock_read(f, rwlock)
```

`lock_read(rwlock)` はリーダー（共有）ロックを取得します。これは [`unlock_read`](@ref) で解放する必要があります。

2 番目のメソッド `lock_read(f, rwlock)` は、リーダーロックを取得した後に引数なしで関数 `f` を実行し、戻る前にそれを解放します。 `lock_read(f, rwlock)` は `f()` の結果を返します。

参照: [`ReadWriteLock`](@ref)
