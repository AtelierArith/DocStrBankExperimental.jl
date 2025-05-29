```
result = henry_coefficient(crystal, molecule, temperature, ljforcefield,
                            insertions_per_volume=200, verbose=true, ewald_precision=1e-6,
                            autosave=true)
```

Conduct particle insertions to compute the Henry coefficient Kₕ of a molecule in a crystal. Also, for free, the heat of adsorption and ensemble average energy of adsorption is computed. The Henry coefficient is a model for adsorption at infinite dilution (low coverage): ⟨N⟩ = Kₕ P, where P is pressure and Kₕ is the Henry coefficient.

Kₕ = β ⟨e^{-β U}⟩, where the average is over positions and orientations of the molecule in the crystal.

# Arguments

  * `crystal::Crystal`: the porous crystal in which we seek to simulate adsorption
  * `molecule::Molecule`: the adsorbate molecule
  * `temperature::Float64`: temperature of bulk gas phase in equilibrium with adsorbed phase in the porous material. units: Kelvin (K)
  * `ljforcefield::LJForceField`: the molecular model used to describe the energetics of the adsorbate-adsorbate and adsorbate-host van der Waals interactions.
  * `insertions_per_volume::Int`: number of Widom insertions to perform for computing the average, per unit cell volume (Å³)
  * `verbose::Bool`: whether or not to print off information during the simulation.
  * `ewald_precision::Float64`: desired precision for Ewald summations; used to determine the replication factors in reciprocal space.
  * `autosave::Bool`: save results file as a .jld2 in rc[:paths][:simulations]
  * `filename_comment::AbstractString`: An optional comment that will be appended to the name of the saved file.

# Returns

  * `result::Dict{String, Float64}`: A dictionary containing all the results from the Henry coefficient simulation
