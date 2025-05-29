```
integrate(system,U; boundary=false)
```

Integrate solution vector region-wise over domain or boundary. The result is an `nspec x nregion` matrix $\int_{\Omega_j} U_i\, dx$ or $\int_{\Gamma_j} U_i\, ds$.
