```
tp_flash(model, p, T, n, method::TPFlashMethod = DETPFlash())
```

Routine to solve non-reactive multicomponent flash problem. The default method uses Global Optimization. see [`DETPFlash`](@ref)

Inputs:

  * T, Temperature
  * p, Pressure
  * n, vector of number of moles of each species

Outputs - Tuple containing:

  * xᵢⱼ, Array of mole fractions of species j in phase i
  * nᵢⱼ, Array of mole numbers of species j in phase i, [mol]
  * G, Gibbs Free Energy of Equilibrium Mixture [J]
