```julia
PseudoFamily(
    identifier::AbstractString
) -> PseudoPotentialData.PseudoFamily

```

`identifier`を表すPseudoFamilyの構築。使用する擬似ポテンシャルファミリーの有効な識別子のリストについては、[`family_identifiers`](@ref)を参照してください。`PseudoFamily`は、元素シンボルから擬似ポテンシャルファイルのフルパスへの`AbstractDict{Symbol,String}`マッピングです。
