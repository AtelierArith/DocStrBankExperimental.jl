```
EI(model::TimeSeriesModel, n, Δ)
```

Compute EI at Fourier frequencies `fftshift(fftfreq(n,2π/Δ))`.

Note internal computation provides values at twice the resolution, this function returns at the desired resolution.
