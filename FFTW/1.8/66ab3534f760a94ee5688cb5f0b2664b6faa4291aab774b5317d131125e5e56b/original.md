```
plan_idct(A [, dims [, flags [, timelimit [, num_threads]]]])
```

Pre-plan an optimized inverse discrete cosine transform (DCT), similar to [`plan_fft`](@ref) except producing a function that computes [`idct`](@ref). The first two arguments have the same meaning as for [`idct`](@ref).
