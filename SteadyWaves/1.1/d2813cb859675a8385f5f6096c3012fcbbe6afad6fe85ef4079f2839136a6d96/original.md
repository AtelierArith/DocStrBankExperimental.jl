```
fourier_approx(d, H, P; pc=1, cc=1, N=10, M=1, g=9.81)
```

Approximate solution `u` of a steady wave of height `H` and length `L` propagating in water of depth `d` using Fourier Approximation Method.

# Arguments

  * `d`: water depth (m)
  * `H`: wave height (m)
  * `P`: wave parameter - length `L` (m) or period `T` (s)
  * `pc`: parameter criterion; `pc=1` - length (default), `pc=2` - period
  * `cc`: current criterion; `cc=1` - Stokes (default), `cc=2` - Euler
  * `N`: number of solution eigenvalues, defaults to `N=10`
  * `M`: number of height steps, defaults to `M=1`
  * `g`: gravity acceleration (m/s^2), defaults to `g=9.81`

# Output

  * `u[1:N+1]`: free surface elevation *kη*
  * `u[N+2:2N+1]`: stream function coefficients *B*
  * `u[2N+2]`: wave celerity *c√(k/g)*
  * `u[2N+3]`: mean water depth *kη̄*
  * `u[2N+4]`: volume flux due to waves *q√(k³/g)*
  * `u[2N+5]`: Bernoulli constant *rk/g*
  * `u[2N+6]`: mean flow velocity *Ū√(k/g)*
  * `u[2N+7]`: wave height *kH*
