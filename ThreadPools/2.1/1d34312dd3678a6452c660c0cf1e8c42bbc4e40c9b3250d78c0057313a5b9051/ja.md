```
tmap(fn, pool, itr)
```

`Base.map`を模倣しますが、関数の評価を提供されたプールに送信してタスクを割り当てます。

# 例

```
julia> pool = twith(ThreadPools.LoggedQueuePool(1,2)) do pool
         tmap(pool, 1:8) do x
           println((x,Threads.threadid()))
         end
       end;
(2, 2)
(1, 1)
(3, 2)
(4, 1)
(5, 2)
(6, 1)
(7, 2)
(8, 1)

julia> plot(pool)
```
