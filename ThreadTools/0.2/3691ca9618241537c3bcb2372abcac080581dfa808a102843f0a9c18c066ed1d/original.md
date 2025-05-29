```
tmap(f, args...)
tmap(f, v, T::DataType)
tmap(f, nthreads::Int, args...)
tmap1(f, args...)
tmap1(f, nthreads::Int, args...)
```

Threaded map. The optional argument `nthreads` limits the number of threads used in parallel. `tmap1` is the same as `tmap`, but falls back to a regular `map` if julia only has access to one thread. If the eltype `T` of the output is specified the call will be type stable.
