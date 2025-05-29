```
morl = Morlet(σ::T) where T <: Real
```

Return the Morlet wavelet with first central frequency parameter `σ`, which controls the time-frequency trade-off. As σ goes to zero, all of the information becomes spatial. Default is `2π`, and it is recommended that you stay within 3-12. Above this range, the overlap between wavelets becomes impractically small. Below it, the mean subtraction term approaches the magnitude of the wavelet, so they become a sum of Gaussians rather than Gaussians.
