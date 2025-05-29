```
Butterworth{T, N}() where {T}
```

Butterwoth filter in the visibility domain, i.e. the fourier-domain profile

$$
    V_N(r) = \left[ 1 + \left( \frac{1}{r}\right)^{2N}  \right]^{-1/2}
$$

i.e. a unit filtering length and unit flux filter. By default if T isn't given, `Butterworth` defaults to `T=Float64`. If futher N isn't given,  `Butterworth` defaults to `N=2`.
