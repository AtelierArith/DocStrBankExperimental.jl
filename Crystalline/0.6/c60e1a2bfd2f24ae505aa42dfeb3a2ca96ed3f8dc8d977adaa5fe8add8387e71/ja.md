```julia
indicator_group_as_string(
    nontriv_Λ::AbstractVector{<:Integer}
)

```

対称性指標群 $X^{\text{BS}}$ をフォーマットされた文字列（すなわち、 `"Zᵢ×Zⱼ×…"` の形式）として返します。ベクトル表現については、[`indicator_group`](@ref)も参照してください。

## 例

```jldoctest
julia> brs = calc_bandreps(2, Val(3));

julia> indicator_group_as_string(brs)
"Z₂×Z₂×Z₂×Z₄"
```
