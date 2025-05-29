```
logqmap(fn, itrs...) -> (pool, collection)
```

Mimics `Base.map`, but launches the function evaluations onto all available  threads, using a queued scheduling strategy appropriate for nonuniform task durations.  Also returns a logged pool that can be analyzed with the  logging functions and `plot`ted.

# Example

```julia
julia> (pool, result) = logqmap(1:8) do x
         println((x,Threads.threadid()))
         x^2
        end;
(3, 3)
(4, 4)
(2, 2)
(5, 3)
(7, 2)
(6, 4)
(8, 3)
(1, 1)

julia> result'
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
1  4  9  16  25  36  49  64

julia> plot(pool)
```

Note that while the execution order is not guaranteed, the result order is.  Also note that the primary thread is used.
