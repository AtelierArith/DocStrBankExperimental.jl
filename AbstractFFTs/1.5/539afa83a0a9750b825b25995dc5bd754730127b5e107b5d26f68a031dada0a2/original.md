```
bfft(A [, dims])
```

Similar to [`ifft`](@ref), but computes an unnormalized inverse (backward) transform, which must be divided by the product of the sizes of the transformed dimensions in order to obtain the inverse. (This is slightly more efficient than [`ifft`](@ref) because it omits a scaling step, which in some applications can be combined with other computational steps elsewhere.)

$$
\operatorname{BDFT}(A)[k] = \operatorname{length}(A) \operatorname{IDFT}(A)[k]
$$
