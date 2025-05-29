```
fit_spectrum(
    hs::Spectrum|HyperSpectrum,
    vq::VectorQuant{S <: Detector, T <: AbstractFloat},
    zero = x -> max(Base.zero(T), x)
)
```

Fit the spectrum or hyper-spectrum using the vector-quant algorithm. The function `zero` is applied to the resultant k-ratios before they are returned.  The default simply sets negative k-ratios to 0.0.  `zero=identity` would leave the negative k-ratios as such.
