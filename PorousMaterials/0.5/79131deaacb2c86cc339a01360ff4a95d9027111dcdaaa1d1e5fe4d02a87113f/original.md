```
repfactors = replication_factors(unitcell, r_cutoff)
```

Find the replication factors needed to make a supercell big enough to fit a sphere with the specified cutoff radius. In PorousMaterials.jl, rather than replicating the atoms in the home unit cell to build the supercell that serves as a simulation box, we replicate the home unit cell to form the supercell (simulation box) in a for loop. This function ensures enough replication factors such that the nearest image convention can be applied.

A non-replicated supercell has 1 as the replication factor in each dimension (`repfactors = (1, 1, 1)`).

# Arguments

  * `unitcell::Box`: The unit cell of the crystal
  * `r_cutoff::Float64`: Cutoff radius beyond which we define the potential energy to be zero (units: Angstrom)

# Returns

  * `repfactors::Tuple{Int, Int, Int}`: The replication factors in the a, b, c directions
