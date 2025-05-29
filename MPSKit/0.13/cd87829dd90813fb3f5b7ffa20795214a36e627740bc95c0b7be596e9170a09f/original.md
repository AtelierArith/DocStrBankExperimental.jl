```julia
struct QuasiparticleAnsatz{A, E} <: MPSKit.Algorithm
```

Optimization algorithm for quasi-particle excitations on top of MPS groundstates.

## Fields

  * `alg::Any`: algorithm used for the eigenvalue solvers
  * `alg_environments::Any`: algorithm used for the quasiparticle environments

## Constructors

```
QuasiparticleAnsatz()
QuasiparticleAnsatz(; kwargs...)
QuasiparticleAnsatz(alg)
```

Create a `QuasiparticleAnsatz` algorithm with the given algorithm, or by passing the  keyword arguments to `Arnoldi`.

## References

  * [Haegeman et al. Phys. Rev. Let. 111 (2013)](@cite haegeman2013)
