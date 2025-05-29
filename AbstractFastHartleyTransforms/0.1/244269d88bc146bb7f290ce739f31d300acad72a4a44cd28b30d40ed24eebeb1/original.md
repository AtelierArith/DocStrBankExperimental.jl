```
plan_fht(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Pre-plan an optimized FHT along given dimensions (`dims`) of arrays matching the shape and type of `A`.  (The first two arguments have the same meaning as for [`fht`](@ref)).) Returns an object `P` which represents the linear operator computed by the FHT, and  which contains all of the information needed to compute `fht(A, dims)` quickly.
