```
logbmap(fn, itrs...) -> (pool, collection)
```

Mimics `Base.map`, but launches the function evaluations onto all available  threads except the primary, using a pre-assigned scheduling strategy  appropriate for uniform task durations.  Also returns a logged pool that can  be analyzed with the logging functions and `plot`ted.

# Example

```julia
julia> (pool, result) = logbmap(1:8) do x
         println((x,Threads.threadid()))
         x^2
       end;
(1, 2)
(6, 4)
(3, 3)
(7, 4)
(2, 2)
(4, 3)
(8, 4)
(5, 3)

julia> result'
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
1  4  9  16  25  36  49  64

julia> plot(pool)
```

Note that while the execution order is not guaranteed, the result order is,  Also note that the primary thread is not used.
