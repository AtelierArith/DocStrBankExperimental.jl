```
tforeach(fn, pool, itr)
```

`Base.foreach`を模倣しますが、関数の評価を提供されたプールに送信してタスクを割り当てます。

# 例

```
julia> pool = twith(ThreadPools.LoggedQueuePool(1,2)) do pool
         tforeach(x -> println((x,Threads.threadid())), pool, 1:8)
       end;
(2, 2)
(1, 1)
(3, 2)
(5, 2)
(4, 1)
(6, 2)
(7, 1)
(8, 2)

julia> plot(pool)
```
