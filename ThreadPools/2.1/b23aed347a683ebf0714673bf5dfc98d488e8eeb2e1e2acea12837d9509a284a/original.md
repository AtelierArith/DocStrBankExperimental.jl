```
@bthreads
```

Mimics `Base.Threads.@threads, but keeps the iterated tasks off if the primary thread.`

# Example

```julia
julia> @bthreads for x in 1:8
         println((x, Threads.threadid()))
       end
(1, 2)
(6, 4)
(3, 3)
(7, 4)
(4, 3)
(8, 4)
(5, 3)
(2, 2)
```

Note that execution order is not guaranteed, but the primary thread does not show up on any of the jobs.
