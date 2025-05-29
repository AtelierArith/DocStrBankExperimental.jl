```
@tthreads pool
```

Mimic the `Base.Threads.@threads` macro, but uses the provided pool to  assign the tasks.

# Example

```
julia> twith(ThreadPools.QueuePool(1,2)) do pool
         @tthreads pool for x in 1:8
           println((x,Threads.threadid()))
         end
       end;
(2, 2)
(3, 2)
(1, 1)
(4, 2)
(5, 1)
(6, 2)
(8, 2)
(7, 1)
```
