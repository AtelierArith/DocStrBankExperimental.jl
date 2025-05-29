```
FrequencySplit([s, ] f::Real) <: Decomposition
```

Similar to the [`Fourier`](@ref) method, but now the "residual" signal is the part of `s` with frequencies higher than `f`, while the "seasonal" part has frequencies `≤ f`.
