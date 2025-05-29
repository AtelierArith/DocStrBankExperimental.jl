```
twith(fn, pool) -> pool
```

Apply the functon `fn` to the provided pool and close the pool.  Returns the  closed pool for any desired analysis or plotting. 

# Example

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

Note in the above example, only two threads were used, as set by the  `QueuePool` setting.
