```
plan_dct(A [, dims [, flags [, timelimit [, num_threads]]]])
```

Pre-plan an optimized discrete cosine transform (DCT), similar to [`plan_fft`](@ref) except producing a function that computes [`dct`](@ref). The first two arguments have the same meaning as for [`dct`](@ref).
