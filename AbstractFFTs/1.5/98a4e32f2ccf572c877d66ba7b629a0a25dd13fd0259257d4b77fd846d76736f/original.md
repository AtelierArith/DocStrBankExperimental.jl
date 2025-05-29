```
rfft(A [, dims])
```

Multidimensional FFT of a real array `A`, exploiting the fact that the transform has conjugate symmetry in order to save roughly half the computational time and storage costs compared with [`fft`](@ref). If `A` has size `(n_1, ..., n_d)`, the result has size `(div(n_1,2)+1, ..., n_d)`.

The optional `dims` argument specifies an iterable subset of one or more dimensions of `A` to transform, similar to [`fft`](@ref). Instead of (roughly) halving the first dimension of `A` in the result, the `dims[1]` dimension is (roughly) halved in the same way.
