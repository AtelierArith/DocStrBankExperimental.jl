```
bforeach(fn, itrs...)
```

Mimics `Base.foreach`, but launches the function evaluations onto all available  threads except the primary, using a pre-assigned scheduling strategy appropriate  for uniform task durations.

# Example

```julia
julia> bforeach(x -> println((x,Threads.threadid())), 1:8)
(1, 2)
(6, 4)
(2, 2)
(7, 4)
(8, 4)
(3, 3)
(4, 3)
(5, 3)
```

Note that the execution order is not guaranteed, and that the primary thread  is not used.
