```
minimized_molecule, min_energy  = find_energy_minimum(xtal, molecule, ljff) # molecule set at initial guess
```

find the minimum energy position, and associated minimum energy, of a molecule in a crystal. n.b. if molecule has more than one atom, it will *not* minimize over the orientation (rotations). the optimizer needs an initial estimate of the minimum energy position. pass molecule with good initial position. if you don't have a good initial position, use [`find_energy_minimum_gridsearch`](@ref).

# Arguments

  * `xtal::Crystal`: the crystal
  * `molecule::Molecule`: the molecule, whose position we seek to tune until we reach a local minimum. must start at a good initial position close to the minimum.
  * `ljff::LJForceField`: the force field used to calculate crystal-molecule interaction energies

# Returns

  * `minimized_molecule::Molecule{Frac}`: the molecule at its minimum energy position
  * `min_energy::Float64`: the associated minimum molecule-crystal interaciton energy (kJ/mol)
