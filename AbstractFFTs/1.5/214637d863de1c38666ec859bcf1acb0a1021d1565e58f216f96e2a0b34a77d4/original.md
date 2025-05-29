```
brfft(A, d [, dims])
```

Similar to [`irfft`](@ref) but computes an unnormalized inverse transform (similar to [`bfft`](@ref)), which must be divided by the product of the sizes of the transformed dimensions (of the real output array) in order to obtain the inverse transform.
