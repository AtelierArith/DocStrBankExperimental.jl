```
compute_rmsd_minimizer(f::AbstractAtomBijection)
compute_rmsd_minimizer(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
compute_rmsd_miminizer(A::AtomTable{T}, B::AtomTable{T})
```

Computes the RMSD-minimizing rigid transformation for the given atom bijection. Defaults to [`TrivialAtomBijection`](@ref) if arguments are atom containers or tables.

# Supported keyword arguments

  * `minimizer::Type{<: AbstractRMSDMinimizer} = RMSDMinimizerCoutsias` Method used for computing the optimal rotation matrix. See [`RMSDMinimizerCoutsias`](@ref) and [`RMSDMinimizerKabsch`](@ref).
