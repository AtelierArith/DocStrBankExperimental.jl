```julia
indicator_group(F::Crystalline.SmithNormalForm.Smith) -> Any

```

Return the symmetry indicator group $X^{\text{BS}}$ associated with an input set of band representations `brs` (or Smith decomposition thereof, `F`), i.e., return the the nontrivial (i.e., ≠ {0,1}) elementary factors of the Smith normal form of the band representation matrix. The return value is a `Vector{Int}` containing the nontrivial factors. If no nontrivial factors exists, the return value is an empty `Vector{Int}`.

See also [`indicator_group_as_string`](@ref) for a formatted string version.

## Understanding

The symmetry indicator group answers the question "what direct product of $\mathbb{Z}_n$ groups is the the quotient group $X^{\text{BS}} = \{\text{BS}\}/\{\text{AI}\}$ isomorphic to?" (see e.g., [Po, Watanabe, & Vishwanath, Nature Commun. **8**, 50 (2017)](https://doi.org/10.1038/s41467-017-00133-2) for more information).

## Example

```jldoctest
julia> brs = calc_bandreps(2, Val(3));

julia> indicator_group(brs)
4-element Vector{Int64}:
 2
 2
 2
 4
```
