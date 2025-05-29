```
atomic_measure(ν::MomentMatrix, rank_check::RankCheck, [dec::LowRankLDLTAlgorithm], [solver::SemialgebraicSets.AbstractAlgebraicSolver])
```

Return an `AtomicMeasure` with the atoms of `ν` if it is atomic or `nothing` if `ν` is not atomic. The `rank_check` and `dec` parameters are passed as is to the [`low_rank_ldlt`](@ref) function. By default, `dec` is an instance of [`SVDLDLT`](@ref). The extraction relies on the solution of a system of algebraic equations. using `solver`. For instance, given a [`MomentMatrix`](@ref), `μ`, the following extract atoms using a `rank_check` of `1e-4` for the low-rank decomposition and homotopy continuation to solve the obtained system of algebraic equations.

```julia
using HomotopyContinuation
solver = SemialgebraicSetsHCSolver(; compile = false)
atoms = atomic_measure(ν, 1e-4, solver)
```

If no solver is given, the default solver of SemialgebraicSets is used which currently computes the Gröbner basis, then the multiplication matrices and then the Schur decomposition of a random combination of these matrices. For floating point arithmetics, homotopy continuation is recommended as it is more numerically stable than Gröbner basis computation.
