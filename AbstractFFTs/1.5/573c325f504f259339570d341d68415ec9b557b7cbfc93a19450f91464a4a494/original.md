```
plan_rfft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Pre-plan an optimized real-input FFT, similar to [`plan_fft`](@ref) except for [`rfft`](@ref) instead of [`fft`](@ref). The first two arguments, and the size of the transformed result, are the same as for [`rfft`](@ref).
