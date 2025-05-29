```
tforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads, using a pre-assigned scheduling strategy appropriate for uniform task durations.

# Example

```julia
julia> tforeach(x -> println((x,Threads.threadid())), 1:8)
(1, 1)
(3, 2)
(5, 3)
(2, 1)
(7, 4)
(4, 2)
(8, 4)
(6, 3)
```

Note that the execution order is not guaranteed, and that the primary thread  is used.
