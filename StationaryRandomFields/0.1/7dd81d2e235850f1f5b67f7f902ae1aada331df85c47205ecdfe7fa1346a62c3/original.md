```
generate_gaussian_noise(data::AbstractNoiseSignal; rng=Random.default_rng())
```

Generate complex gausisian noises on Fourier space over the frequency space expected for Real FFT. This return a complex array, which is consistent with Fourier-domain representation of a real uncorrelated Gaussian noise with the zero mean and variance of `sizeof(data)` in signal-domain. The size of the output array is given by `rfftsize(data)`.
