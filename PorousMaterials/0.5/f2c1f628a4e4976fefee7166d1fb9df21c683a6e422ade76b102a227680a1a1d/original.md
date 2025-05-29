energy = vdw_energy(crystal, molecule, ljforcefield)

Calculates the van der Waals interaction energy between a molecule and a crystal. Applies the nearest image convention to find the closest replicate of a specific atom.

WARNING: it is assumed that the framework is replicated sufficiently such that the nearest image convention can be applied. See [`replicate`](@ref) and [`replication_factors`](@ref).
