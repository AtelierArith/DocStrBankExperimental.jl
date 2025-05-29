```
integrate(system,F, Ut; boundary=false, data=system.physics.data)
```

Integrate transient solution vector region-wise over domain or boundary. The result is an `nspec x nregion x nsteps` DiffEqArray $\int_{\Omega_j} F_i(U_k)\, dx$ or $\int_{\Gamma_j} F_i(U_k)\, ds$.
