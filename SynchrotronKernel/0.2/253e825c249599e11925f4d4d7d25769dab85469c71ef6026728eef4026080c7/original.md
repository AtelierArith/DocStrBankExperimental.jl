```
synchrotron_intensity(x::Real)
```

Computes the total synchrotron kernel, without polarisation components. Wrapper for [`F`](@ref).

$F(x) = x \int_x^\infty K_{\frac{5}{3}}(t) dt$
