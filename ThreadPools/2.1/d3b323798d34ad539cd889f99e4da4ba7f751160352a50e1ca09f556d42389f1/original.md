```
tmap(fn, itrs...) -> collection
```

Mimics `Base.map`, but launches the function evaluations onto all available  threads, using a pre-assigned scheduling strategy appropriate for uniform task durations.

# Example

```julia
julia> tmap(x -> begin; println((x,Threads.threadid())); x^2; end, 1:8)'
(7, 4)
(5, 3)
(8, 4)
(1, 1)
(6, 3)
(2, 1)
(3, 2)
(4, 2)
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
 1  4  9  16  25  36  49  64
```

Note that while the execution order is not guaranteed, the result order is.  Also note that the primary thread is used.
