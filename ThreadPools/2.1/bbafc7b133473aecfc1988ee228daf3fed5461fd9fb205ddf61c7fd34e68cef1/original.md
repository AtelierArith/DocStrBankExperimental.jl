```
tforeach(fn, pool, itr)
```

Mimics `Base.foreach`, but launches the function evaluations onto the provided  pool to assign the tasks.

# Example

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
