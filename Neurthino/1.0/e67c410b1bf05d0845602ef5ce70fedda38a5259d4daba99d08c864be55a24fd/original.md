```julia
MatterOscillationMatrices(
    osc_vacuum,
    energy,
    density;
    zoa,
    anti
)

```

Create modified oscillation parameters for neutrino propagation through matter

# Arguments

  * `osc_vacuum::OscillationParameters`: Oscillation parameters in vacuum
  * `energy`: Neutrino energy [GeV]
  * `density`: Matter density in g*cm^-3
  * `zoa`: Proton nucleon ratio (Z/A)
  * `anti`: Is anti neutrino
