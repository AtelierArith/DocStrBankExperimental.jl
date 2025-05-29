```
qmap(fn, itrs...) -> collection
```

Mimics `Base.map`, but launches the function evaluations onto all available  threads, using a queued scheduling strategy appropriate for nonuniform task durations.

# Example

```julia
julia> qmap(x -> begin; println((x,Threads.threadid())); x^2; end, 1:8)'
(2, 3)
(3, 2)
(4, 4)
(5, 3)
(6, 2)
(7, 4)
(8, 3)
(1, 1)
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
 1  4  9  16  25  36  49  64
```

Note that while the execution order is not guaranteed, the result order is.  Also note that the primary thread is used.
