```
 pfm2hr(A::PeriodicFunctionMatrix; nsample, NyquistFreq) -> Ahr::HarmonicArray
```

Convert a periodic function matrix into a harmonic array representation.  If `A(t)` is a periodic function matrix of period `T`, then the harmonic array representation `Ahr` is determined by applying the fast Fourier transform to the sampled arrays `A(iΔ)`, `i = 0, ..., k`, where `Δ = T/k` is the sampling period and `k` is the number of samples specified by the keyword argument `nsample = k` (default: `k = 128`). If the Nyquist frequency `f` is specified via the keyword argument `NyquistFreq = f`, then `k` is chosen `k = 2*f*T` to avoid signal aliasing.     
