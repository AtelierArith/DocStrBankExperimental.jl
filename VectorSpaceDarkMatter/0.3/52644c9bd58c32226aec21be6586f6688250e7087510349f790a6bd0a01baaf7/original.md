```
GaussianF(c::Float64, uSph::Vector{Float64}, sigma::Float64)
```

Contains parameters for a gaussian function where `uSph` is the spherical vector indicating the center of the gaussian, `uSph = (u, theta, phi)`. `sigma` is the dispersion (equal to $\sqrt{2} \sigma$ in a "normal" gaussian).  `c` is the overall amplitude. `u` and `sigma` should have the same units.

An instance `g` of `GaussianF` is callable by `g(uvec)`, which will evaluate the gaussian at `uvec = [u, theta, phi]`.
