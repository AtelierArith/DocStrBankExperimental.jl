```
ϕ = electrostatic_potential_energy(crystal, molecule, eparams, eikr)
```

Compute the electrostatic potential energy of a molecule inside a crystal.

The electrostatic potential is created by the point charges assigned to the crystal atoms in `crystal.charges`. Periodic boundary conditions are applied through the Ewald summation. The spurious self-interaction term is neglected here because we are looking at *differences* in energy in a Monte Carlo simulation.

Warning: it is assumed that the crystal is replicated enough such that the nearest image convention can be applied for the short-range cutoff radius supplied in `eparams.sr_cutoff_r`.

# Arguments

  * `crystal::Crystal`: Crystal structure (see `crystal.charges` for charges)
  * `molecule::Molecule`: The molecule being compared to the atoms in the crystal.
  * `eparams::EwaldParams`: data structure containing Ewald summation settings
  * `eikr::Eikr`: Stores the eikar, eikbr, and eikcr OffsetArrays used in this calculation.

# Returns

  * `pot::EwaldSum`: Electrostatic potential between `crystal` and `molecule` (units: K)
