```julia
struct ChepigaAnsatz{A<:KrylovKit.KrylovAlgorithm} <: MPSKit.Algorithm
```

Single-site optimization algorithm for excitations on top of MPS groundstates.

## Fields

  * `alg::KrylovKit.KrylovAlgorithm`: algorithm used for the eigenvalue solvers

## Constructors

```
ChepigaAnsatz()
ChepigaAnsatz(; kwargs...)
ChepigaAnsatz(alg)
```

Create a `ChepigaAnsatz` algorithm with the given eigensolver, or by passing the keyword arguments to [`Arnoldi`][@extref KrylovKit.Arnoldi].

## References

  * [Chepiga et al. Phys. Rev. B 96 (2017)](@cite chepiga2017)
