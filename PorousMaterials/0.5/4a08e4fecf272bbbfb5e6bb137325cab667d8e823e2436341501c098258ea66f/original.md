```
ϕ = electrostatic_potential_energy(molecules, eparams, box, eikr)
```

Compute the electrostatic potential energy of a system comprised of an array of `Molecule`s.

The EWald summation is used here in a double for loop; do not use this function for Monte Carlo simulations because it is computationally expensive.

Returns an `EwaldSum` type containing short-range and long-range contributions to the Ewald sum as well as the spurious self-interaction and intramolecular interactions. Access via (ϕ.sr, ϕ.lr, ϕ.self, ϕ.intra).

Units of energy: Kelvin

# Arguments

  * `molecules::Array{Molecules, 1}`: array of molecules comprising the system.
  * `eparams::EwaldParams`: data structure containing Ewald summation settings
  * `box::Box`: the box the energy is being computed in
  * `eikr::Eikr`: Stores the eikar, eikbr, and eikcr OffsetArrays used in this calculation.

# Returns

  * `ϕ::GGEwaldSum`: The total electrostatic potential energy
