```
gamma_c_target(surfaces, eq, ζ_range, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surfaces, eq, ζMin, ζStep, ζMax, BResolution, epsEff = true, gammaC = true)
gamma_c_target(surfaces, eq, ζMin, ζStep, ζMax, BResolution, comm, epsEff = true, gammaC = true)
```

Function to calculate $\Gamma_c$ from one or several surfaces (with or without MPI)

# Arguments

  * `surfaces::Union{T, Vector{T}}`: a single float or vector of floats giving the surface at which to compute $\Gamma_c$. These values are given in normalized toroidal flux, $s$
  * `eq::E`: A Vmec or DESC equilibrium
  * `BResolution::Int`: The resolution for the B field integration
  * `comm::MPI:Comm`: If included the code will use the MPI interface to speed computation
  * `epsEff::Bool=true`: Optional argument default true. if true, code will calculate and return the value of $\epsilon_\mathrm{eff}$
  * `gammac::Bool=true`: Optional argument default true. if true, code will calculate and return the value of $\Gamma_c$

# Outputs:

  * `targetValues::Vector{T}`: an array of values computing $\epsilon_\mathrm{eff}$ and/or $\Gamma_c$ depending on the optional bool arguments. In case both are present (default) they are returned in the form in pairs of $(\epsilon_\mathrm{eff}, \Gamma_c)$
