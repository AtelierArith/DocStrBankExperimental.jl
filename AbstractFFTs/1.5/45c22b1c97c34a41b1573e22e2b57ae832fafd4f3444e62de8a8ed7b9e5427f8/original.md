```
plan_bfft(A [, dims]; flags=FFTW.ESTIMATE, timelimit=Inf)
```

Same as [`plan_fft`](@ref), but produces a plan that performs an unnormalized backwards transform [`bfft`](@ref).
