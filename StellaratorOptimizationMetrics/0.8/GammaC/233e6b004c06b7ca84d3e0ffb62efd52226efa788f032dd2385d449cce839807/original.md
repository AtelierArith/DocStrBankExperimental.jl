```
gamma_c_target(surface, ζ_range, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surf, ζMin, ζStep, ζMax, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surf, ζMin, ζStep, ζMax, BResolution, comm, epsEff = true, gammaC = true)
```

# Arguments

  * `surf::Surface`: A VMEC or DESC surface (code needs either an Equilibrium and a list of surfaces, or a single surface)
  * `ζ_range <: AbstractRange`: Range of toroidal angle values in radians
  * `BResolution::Int`: The resolution for the B field integration
  * `comm::MPI:Comm`: If included the code will use the MPI interface to speed computation
  * `epsEff::Bool=true`: Optional argument default true. if true, code will calculate and return the value of $\epsilon_\mathrm{eff}$
  * `gammac::Bool=true`: Optional argument default true. if true, code will calculate and return the value of $\Gamma_c$

# Outputs:

  * Tuple of values computing $\epsilon_\mathrm{eff}$ and/or $\Gamma_c$ depending on the optional bool arguments. In case both are present (default) they are returned in the form in pairs of $(\epsilon_\mathrm{eff}, \Gamma_c)$
