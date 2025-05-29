```
total_ϕ = total_electrostatic_potential_energy(crystal, molecules, eparams, eikr)
```

Explanation of total*electrostatic*potential_energy that uses crystal

# Arguments

  * `crystal::Crystal`: Crystal structure (see `crystal.charges` for charges)
  * `molecules::Array{Molecule, 1}`: The molecules comprising the system.
  * `eparams::EwaldParams`: data structure containing Ewald summation settings
  * `eikr::Eikr`: Stores the eikar, eikbr, and eikcr OffsetArrays used in this calculation.
