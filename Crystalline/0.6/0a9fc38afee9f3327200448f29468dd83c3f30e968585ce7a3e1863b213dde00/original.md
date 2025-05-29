```julia
calc_topology(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_incompatible,
    allow_negative
) -> Crystalline.TopologyKind

```

Return whether a symmetry vector `n` is a band-combination that is trivial or nontrivial from a symmetry perspective, i.e. whether it has an integer-coefficient expansion in the elementary band representation (EBR) basis or not (i.e. a rational-coefficient expansion). Returns a value from the Enum [`TopologyKind`](@ref) (`TRIVIAL` or `NONTRIVIAL`).

No distinction is made between fragile and trivial symmetry vectors: i.e., a `TRIVIAL` return value may in fact be a `FRAGILE` state on more careful inspection: such a distinction can be made by `calc_detailed_topology` from [SymmetryBases.jl](https://github.com/thchr/SymmetryBases.jl)

See also [`symmetry_indicators`](@ref) to obtain the associated symmetry indicators of a nontrivial symmetry vector.

## Input

The EBR basis can be provided as `::BandRepSet`, `::Matrix{<:Integer}`, or a `Smith` decomposition. The length of `n` must equal the EBR basis' number of irreps or the number of irreps plus 1 (i.e. include the band connectivity).

## Implementation

We check whether an integer-coefficient expansion exists via the Smith normal decomposition of the EBR matrix $\mathbf{B} = \mathbf{S}\boldsymbol{\Lambda}\mathbf{T}$. If

$$
    (\mathbf{S}^{-1}\mathbf{n})_j = 0 \mod \lambda_j
$$

for all $j = 1, \ldots, d^{\text{bs}}$ ($d^{\text{bs}}$ is the number of non-zero diagonal elements of $\boldsymbol{\Lambda}$, i.e. the invariant factors of $\mathbf{B}$), there exists a solution to $\mathbf{B}\mathbf{c} = \mathbf{n}$ with integer coefficients $c_j \in \mathbb{Z}$.

## Keyword arguments

If `n` is not a compatible band structure (i.e., if `iscompatible(n, [...]) = false`), an error is thrown. This behavior can be controlled by two boolean keyword arguments:

  * `allow_incompatible` (`false`): if `true`, disables the compatibility check entirely.
  * `allow_negative` (`false`): if `true`, allows negative symmetry content, but maintain requirement that `n` respects the compatibilty relations in an algebraic sense.
