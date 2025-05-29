```
plan_brfft(A, d [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Pre-plan an optimized real-input unnormalized transform, similar to [`plan_rfft`](@ref) except for [`brfft`](@ref) instead of [`rfft`](@ref). The first two arguments and the size of the transformed result, are the same as for [`brfft`](@ref).
