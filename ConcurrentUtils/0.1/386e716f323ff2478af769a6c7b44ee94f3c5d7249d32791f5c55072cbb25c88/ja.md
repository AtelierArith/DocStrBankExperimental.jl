```
trylock_read(rwlock) -> acquired::Bool
```

リーダーロックを取得しようとします。成功した場合は`true`を返します。

この関数はロックフリーですが、効率的でない場合があります。

参照: [`ReadWriteLock`](@ref)
