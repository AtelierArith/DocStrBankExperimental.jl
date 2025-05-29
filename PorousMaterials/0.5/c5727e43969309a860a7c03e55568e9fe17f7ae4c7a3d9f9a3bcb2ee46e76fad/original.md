```
forcefield_coverage(atoms, ljforcefield)
forcefield_coverage(molecule, ljforcefield)
forcefield_coverage(crystal, ljforcefield)
```

Check that the force field contains parameters for every `species` in `atoms::Atoms`. Will print out which atoms are missing.

# Arguments

  * `atoms::Atoms`: a set of atoms
  * `ljforcefield::LJForceField`: A Lennard Jones forcefield object containing information on atom interactions

# Returns

  * `all_covered::Bool`: returns true if all species in the atoms are covered by the force field.
