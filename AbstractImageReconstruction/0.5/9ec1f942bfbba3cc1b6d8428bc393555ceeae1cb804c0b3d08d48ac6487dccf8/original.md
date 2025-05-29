```
reconstruct(algo::T, u) where {T<:AbstractImageReconstructionAlgorithm}
```

Reconstruct an image from input `u` using algorithm `algo`. The `àlgo` will be `lock`ed until the result is available or an error occurs.
