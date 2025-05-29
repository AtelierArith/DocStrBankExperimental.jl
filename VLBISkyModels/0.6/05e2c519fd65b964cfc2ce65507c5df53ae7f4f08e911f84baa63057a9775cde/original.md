```julia
struct FFTAlg{T} <: VLBISkyModels.FourierTransform
```

Use an FFT to compute the approximate numerical visibilitymap of a model. For a DTFT see [`DFTAlg`](@ref DFTAlg) or for an NFFT [`NFFTAlg`](@ref NFFTAlg)

# Fields

  * `padfac`: The amount to pad the image by. Note we actually round up to use small prime factor.

  * `flags`: FFTW flags or wisdom for the transformation. The default is `FFTW.ESTIMATE`, but you can use `FFTW.MEASURE` for better performance if you plan on evaluating the sample FFT multiple times.
