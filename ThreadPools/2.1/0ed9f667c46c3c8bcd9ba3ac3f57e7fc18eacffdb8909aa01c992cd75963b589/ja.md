```
twith(fn, pool) -> pool
```

提供されたプールに関数 `fn` を適用し、プールを閉じます。分析やプロットのために閉じたプールを返します。

# 例

```
julia> twith(ThreadPools.QueuePool(1,2)) do pool
         tforeach(x -> println((x,Threads.threadid())), pool, 1:8)
       end;
(2, 2)
(1, 1)
(3, 2)
(4, 1)
(5, 2)
(6, 1)
(7, 2)
(8, 1)
```

上記の例では、`QueuePool` 設定によって設定されたように、2つのスレッドのみが使用されたことに注意してください。
