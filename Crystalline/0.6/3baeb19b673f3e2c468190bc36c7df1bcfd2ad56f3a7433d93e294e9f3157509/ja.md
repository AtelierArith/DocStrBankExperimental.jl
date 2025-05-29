```
@composite cᵢ*brs[i] + cⱼ*brs[j] + … + cₖ*brs[k]
```

単一のバンド表現変数、例えば `Collection{<:NewBandRep}` 型の `brs` を要素 `brs[i]` への参照と関連する整数係数 `cᵢ` を用いた式から整数係数の `CompositeBandRep` を作成するための便利なマクロです。

より明示的には、`@composite cᵢ*brs[i] + cⱼ*brs[j] + … + cₖ*brs[k]` は `CompositeBandRep(coefs, brs)` を作成し、ここで `coefs[n]` は `i == n` のための `cᵢ` の合計に等しくなります。

[`CompositeBandRep`](@ref) および [`Crystalline.CompositeBandRep_from_indices`](@ref) も参照してください。

## 例

```jldoctest composite
julia> brs = calc_bandreps(2, Val(3));

julia> cbr = @composite 3brs[1] + 2brs[2] - brs[3] - brs[4]
16-irrep CompositeBandRep{3}:
 3(1h|Ag) + 2(1h|Aᵤ) - (1g|Ag) - (1g|Aᵤ) (3 bands)

julia> n = 3brs[1] + 2brs[2] - brs[3] - brs[4]
16-irrep SymmetryVector{3}:
 [Z₁⁺+2Z₁⁻, Y₁⁺+2Y₁⁻, 2U₁⁺+U₁⁻, X₁⁺+2X₁⁻, 2T₁⁺+T₁⁻, 2Γ₁⁺+Γ₁⁻, 2V₁⁺+V₁⁻, R₁⁺+2R₁⁻] (3 bands)

julia> SymmetryVector(cbr) == n
true
```

係数は正または負の整数であり、バンド表現に左または右から掛けられます。左からの場合、`*` は省略可能です：

```jldoctest composite
julia> @composite -brs[1] + brs[2]*3 - brs[7]*(-2) + (-3)*brs[end-2]
16-irrep CompositeBandRep{3}:
 -(1h|Ag) + 3(1h|Aᵤ) + 2(1e|Ag) - 3(1b|Aᵤ) (1 band)
```

## 制限事項

  * 係数はリテラルでなければなりません：すなわち、変数 `c` を含む `c*brs[1]` のような項はサポートされていません。
  * 係数は整数でなければなりません：すなわち、有理数係数はサポートされていません。
  * 係数は式であってはなりません：すなわち、`(2+2)brs[1]`、`22*2brs[1]`、または `2*brs[3]*4` のような項はサポートされておらず、未定義の動作を引き起こし、静かに間違った結果をもたらす可能性があります。
