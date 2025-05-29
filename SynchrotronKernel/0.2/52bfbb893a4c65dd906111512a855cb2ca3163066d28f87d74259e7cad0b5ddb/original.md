```
synchrotron_kernel(x::Real)
```

Computes the first synchrotron function and the polarisation components at a given frequency ratio $x = \frac{\nu}{\nu_0}$. Returns a tuple `(K_tot, K_ort, K_par)`.

```julia
K_tot = F(x)
K_ort = 0.5 * (F(x) + G(x))
K_par = 0.5 * (F(x) - G(x))
```

## Synchrotron Functions

$F(x) = x \int_x^\infty K_{\frac{5}{3}}(t) dt$

$G(x) = x K_{\frac{2}{3}}(x)$
