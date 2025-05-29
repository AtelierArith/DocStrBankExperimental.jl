```
memory_limit!(soft_limit::Integer, hard_limit::Integer = -1)
```

現在のJuliaプロセスの仮想メモリ制限を設定します。

`soft_limit`と`hard_limit`はバイト単位です。`-1`の値は無制限を意味します。`hard_limit`は`soft_limit`よりも厳しく設定してはいけなく、通常は`-1`に設定するべきです。

`(soft_limit::Int64, hard_limit::Int64)`を返します。

!!! note
    現在、Linuxでのみ効果があり、他のオペレーティングシステムでは何もせず、単に`(Int64(-1), Int64(-1))`を返します。

