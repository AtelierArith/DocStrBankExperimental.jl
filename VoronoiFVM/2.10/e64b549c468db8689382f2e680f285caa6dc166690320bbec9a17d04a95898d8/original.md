```
integrate(system,F,U; boundary=false, data=system.physics.data)
```

Integrate node function (same signature as reaction or storage)  `F` of  solution vector `U` region-wise over domain or boundary. The result is an `nspec x nregion` matrix $\int_{\Omega_j} F_i(U)\, dx$ or $\int_{\Gamma_j} F_i(U)\, ds$.
