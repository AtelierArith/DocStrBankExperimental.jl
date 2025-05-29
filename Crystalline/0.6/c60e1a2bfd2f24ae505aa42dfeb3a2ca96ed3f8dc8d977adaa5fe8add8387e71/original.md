```julia
indicator_group_as_string(
    nontriv_Λ::AbstractVector{<:Integer}
)

```

Return the symmetry indicator group $X^{\text{BS}}$ as a formatted string (i.e.,  as `"Zᵢ×Zⱼ×…"`). See also [`indicator_group`](@ref) for a vector representation.

## Example

```jldoctest
julia> brs = calc_bandreps(2, Val(3));

julia> indicator_group_as_string(brs)
"Z₂×Z₂×Z₂×Z₄"
```
