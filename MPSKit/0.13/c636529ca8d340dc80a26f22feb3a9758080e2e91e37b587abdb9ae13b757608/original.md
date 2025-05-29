```
ChepigaAnsatz2 <: Algorithm
```

Two-site optimization algorithm for excitations on top of MPS groundstates.

## Fields

  * `alg::A = Defaults.eigsolver`: algorithm to use for the eigenvalue problem.
  * `trscheme = Defaults.trscheme`: algorithm to use for truncation.

## Constructors

```
ChepigaAnsatz2()
ChepigaAnsatz2(; kwargs...)
ChepigaAnsatz2(alg, trscheme)
```

Create a `ChepigaAnsatz2` algorithm with the given eigensolver and truncation, or by passing the keyword arguments to `Arnoldi`.

## References

  * [Chepiga et al. Phys. Rev. B 96 (2017)](@cite chepiga2017)
