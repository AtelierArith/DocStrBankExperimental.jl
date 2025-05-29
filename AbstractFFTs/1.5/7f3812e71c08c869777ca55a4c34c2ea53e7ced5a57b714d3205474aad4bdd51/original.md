```
plan_irfft(A, d [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Pre-plan an optimized inverse real-input FFT, similar to [`plan_rfft`](@ref) except for [`irfft`](@ref) and [`brfft`](@ref), respectively. The first three arguments have the same meaning as for [`irfft`](@ref).
