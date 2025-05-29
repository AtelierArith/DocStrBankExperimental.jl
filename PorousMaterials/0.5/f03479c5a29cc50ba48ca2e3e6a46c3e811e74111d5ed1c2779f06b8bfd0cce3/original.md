```
total_ϕ = total_electrostatic_potential_energy(molecules, eparams, box, eikr)
```

Calculates the total electrostatic potential energy of an array of `Molecule`s using a Grand Canonical Monte Carlo (GCMC) algorithm. #TODO add to this

# Arguments

  * `molecules::Array{Molecule, 1}`: The molecules comprising the system.
  * `eparams::EwaldParams`: data structure containing Ewald summation settings
  * `box::Box`: The box the energy is being computed in.
  * `eikr::Eikr`: Stores the eikar, eikbr, and eikcr OffsetArrays used in this calculation.

# Returns

  * `ϕ::GGEwaldSum`: The total electrostatic potential energy
