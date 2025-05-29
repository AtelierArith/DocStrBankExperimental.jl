```
Sinusoidal(fs)
```

Decompose a timeseries `s` into a **sum** `x + r`, where `x` are sinusoidal components with the given frequencies `fs` that minimize coefficients $A, \phi$ of the expression

$$
s \approx A_0 + \sum_i A_i \cos(2\pi f_i t + \phi_i)
$$

with $A_0 = \bar{s}$ the mean.

This method uses a new least-squares algorithm in frequency domain using the package [LPVSpectral.jl](https://github.com/baggepinnen/LPVSpectral.jl), see[^Bagge2017]. It works for non-equispaced `t` axis (and also normal), is generally very accurate (if choosen frequencies are not too close), but has performance scaling of O(N^2.4) instead of O(n log(n)) of [`Fourier`](@ref).

Because it can work with arbitrary signal length the method always estimates the zero-frequency Fourier component, and attributes it to `x`. The fitted coefficients $A, \phi$ are available as fields `.A` and `.φ` of the struct (first entry is zero-frequency component $A_0, \phi_0$).

[^Bagge2017]: F. Bagge Carlson et al., [Linear Parameter-Varying Spectral Decomposition](https://lup.lub.lu.se/search/publication/ac32368e-e199-44ff-b76a-36668ac7d595).
