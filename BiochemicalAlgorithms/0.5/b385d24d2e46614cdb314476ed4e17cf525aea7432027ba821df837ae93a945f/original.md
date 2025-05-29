```
map_rigid!(f::AbstractAtomBijection)
map_rigid!(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
map_rigid!(A::AtomTable{T}, B::AtomTable{T})
```

Computes, applies, and returns the RMSD-minimizing rigid transformation for the given atom bijection. Defaults to [`TrivialAtomBijection`](@ref) if arguments are atom containers or tables. Only the first structure (`A`) is modified, i.e. mapped onto the second one (`B`).

# Supported keyword arguments

  * `heavy_atoms_only::Bool = false` If `true`, hydrogen atoms are ignored during the computation of the optimal transformation. Otherwise, all atoms are used.
  * `minimizer::Type{<: AbstractRMSDMinimizer} = RMSDMinimizerCoutsias` See [`compute_rmsd_minimizer`](@ref)
