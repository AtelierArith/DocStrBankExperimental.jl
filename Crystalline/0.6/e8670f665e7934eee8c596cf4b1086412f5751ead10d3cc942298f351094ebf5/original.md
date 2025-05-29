```julia
symmetry_indicators(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_incompatible,
    allow_negative
) -> Any

```

Return the symmetry indicator indices of a symmetry vector `n`, in the context of a set of elementary band representations (EBRs) `brs`, provided as a `Collection{<:NewBandRep}`, a `BandRepSet`, a `Matrix{<:Integer}`, or a `Smith` decomposition thereof.

In detail, the method returns the nontrivial indices $[\nu_1, \ldots, \nu_n]$ associated with the symmetry indicator group (see, [`indicator_group`](@ref)) $[\lambda_1, \ldots, \lambda_n]$ of the EBR basis. The indices $\nu_i$ are elements of a cyclic group of order $\lambda_i$, i.e.  $\nu_i ∈ \mathbb{Z}_{\lambda_i} = \{0, 1, \ldots, \lambda_i-1\}$.

See also `calc_topology` to determine whether any symmetry indicator is nonzero (i.e., whether the symmetry vector is topologically nontrivial).

## Implementation

The indices are computed using the Smith normal decomposition $\mathbf{B} = \mathbf{S} \boldsymbol{\Lambda}\mathbf{T}$ of the EBR matrix $\mathbf{B}$.  Specifically, denoting by $\mathbf{s}_i^{-1}$ the $i$th nontrivial row of $\mathbf{S}^{-1}$, the symmetry indicator topological indices of a symmetry vector $\mathbf{n}$ are computed as $\nu_i = \mathbf{s}_i^{-1}\mathbf{n}$.[^HCP]

[^HCP]: [H.C. Po, J. Phys. Cond. Matter **32**, 263001 (2020)](https://doi.org/10.1088/1361-648X/ab7adb).

## Keyword arguments

If `n` is not a compatible band structure (i.e., if `iscompatible(n, brs) = false`), an error is thrown. This behavior can be controlled by two boolean keyword arguments:

  * `allow_incompatible` (`false`): if `true`, disables the compatibility check entirely.
  * `allow_negative` (`false`): if `true`, allows negative symmetry content, but maintain requirement that `n` respects the compatibilty relations in an algebraic sense.
