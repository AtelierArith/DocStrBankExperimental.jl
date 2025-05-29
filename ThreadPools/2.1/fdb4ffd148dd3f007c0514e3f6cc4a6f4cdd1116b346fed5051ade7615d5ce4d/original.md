```
qbmap(fn, itrs...) -> collection
```

Mimics `Base.map`, but launches the function evaluations onto all available  threads except the primary, using a queued scheduling strategy appropriate  for nonuniform task durations.

# Example

```julia
julia> qbmap(x -> begin; println((x,Threads.threadid())); x^2; end, 1:8)'
(2, 3)
(1, 2)
(3, 4)
(5, 2)
(4, 3)
(6, 4)
(7, 2)
(8, 3)
1×8 LinearAlgebra.Adjoint{Int64,Array{Int64,1}}:
 1  4  9  16  25  36  49  64
```

Note that while the execution order is not guaranteed, the result order is,  Also note that the primary thread is not used.
