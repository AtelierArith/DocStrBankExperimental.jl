```
kernfft = freqkernel([T::Type], kern, sz=size(kern); rfft=false)
```

Return a frequency-space representation of `kern`. This embeds `kern` in an array of size `sz`, in a manner that implicitly imposes periodic boundary conditions, and then returns the Fourier transform (frequency response). This is sometimes called the optical transfer function, and is known in some frameworks as `psf2otf`. If `rfft` is `true`, the FFT for real-valued arrays (`rfft`) is returned instead and the first dimension size will be approximately half of `sz[1]`.

`kern` should be zero-centered, i.e., `kern[0, 0]` should reference the center of your kernel, and `sz` must be large enough to support `kern`. See [`centered`](@ref OffsetArrays.centered). Optionally specify the numeric type `T` (which must be one of the types supported by FFTW, either `Float32` or `Float64`).

The inverse of `freqkernel` is [`spacekernel`](@ref).
