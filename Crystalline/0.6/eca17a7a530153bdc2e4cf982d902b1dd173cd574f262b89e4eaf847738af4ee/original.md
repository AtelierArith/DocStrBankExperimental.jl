```julia
iscompatible(
    n::AbstractVector{<:Integer},
    F::Crystalline.SmithNormalForm.Smith;
    allow_negative
) -> Any

```

Test whether a symmetry vector `n` is a valid band grouping, i.e. whether it fulfils all compatibility relations in the Brillouin zone and is non-negative. That is, test whether `n` belong to the set of physical band structures {BS}.

The test compares the symmetry vector `n` to an set of elementary band representations, provided either as a `BandRepSet`, a `Collection{<:NewBandRep}`, a `Matrix{<:Integer}`, or a `Smith` decomposition. The irrep sorting of `n` and this set of EBRs must be identical.

## Keyword arguments

  * `allow_negative` (`false`): if `true`, allows negative symmetry content. This can be relevant if `n` contains negative content that may nevertheless respect the compatibility relations in a strictly algebraic sense.

## Implementation

Belonging to {BS} is tested by comparing to a set of elementary band representations (EBRs). A symmetry vector $\mathbf{n}$ is in {BS} if

$$
    \tilde{\mathbf{S}}\tilde{\mathbf{S}}^{-1}\mathbf{n} = \mathbf{n}
$$

where $\tilde{\mathbf{S}}$ ($\tilde{\mathbf{S}}^{-1}$) denotes the nonsingular columns (rows) of $\mathbf{S}$ ($\mathbf{S}^{-1}$) in the Smith normal decomposition of the EBR matrix $\mathbf{A} = \mathbf{S}\boldsymbol{\Lambda}\mathbf{T}$.

## Examples

```julia-repl
julia> brs = calc_bandreps(22, Val(3)); # from Crystalline.jl
julia> n = parse(SymmetryVector, "Z₃, T₃, L₁, Y₃, Γ₃", irreps(brs)) # a compatible vector

# test a compatible symmetry vector
julia> iscompatible(n, brs)
true

# test an invalid symmetry vector
julia> n′ = copy(n);
julia>  n′.multsv[1] .= [1,0,0,0]  # change Z₃ to Z₁; incompatible modification
julia> iscompatible(n′, brs)
false

# test a symmetry vector with negative content
julia> n′′ = brs[1] + brs[2] - brs[3];  # contains negative elements
julia> iscompatible(n′′, brs)
false
julia> iscompatible(n′′, brs; allow_negative=true)
true
```
