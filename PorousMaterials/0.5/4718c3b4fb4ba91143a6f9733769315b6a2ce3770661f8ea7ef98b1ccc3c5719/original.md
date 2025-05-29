```
ljforcefield = LJForceField(forcefield; r_cutoff=14.0, mixing_rules="Lorentz-Berthelot")
```

Read a .csv file containing Lennard Jones parameters (with the following columns: `atom,sigma,epsilon` and constructs a LJForceField object.

The following mixing rules are implemented:

  * Kong mixing rules: DOI 10.1063/1.1680358
  * Lorentz-Berthelot: https://en.wikipedia.org/wiki/Combining*rules#Lorentz-Berthelot*rules
  * Geometric

# Arguments

  * `forcefield::String`: name of the forcefield.
  * `r_cutoff::Float64`: cutoff radius beyond which we define the potential energy to be zero (units: Angstrom)
  * `mixing_rules::String`: The mixing rules used to compute the cross-interaction terms of the forcefield

# Returns

  * `ljforcefield::LJForceField`: The data structure containing the forcefield parameters (pure σ, ϵ and cross interaction terms as well)
