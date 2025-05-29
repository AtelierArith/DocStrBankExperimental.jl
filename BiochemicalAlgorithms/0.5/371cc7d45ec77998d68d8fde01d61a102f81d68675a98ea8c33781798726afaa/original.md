```
compute_rmsd(f::AbstractAtomBijection)
compute_rmsd(A::AbstractAtomContainer{T}, B::AbstractAtomContainer{T})
compute_rmsd(A::AtomTable{T}, B::AtomTable{T})
```

Computes the [root mean square deviation (RMSD)](https://en.wikipedia.org/wiki/Root-mean-square_deviation_of_atomic_positions) of the given atom bijection. Defaults to [`TrivialAtomBijection`](@ref) if arguments are atom containers or tables.
