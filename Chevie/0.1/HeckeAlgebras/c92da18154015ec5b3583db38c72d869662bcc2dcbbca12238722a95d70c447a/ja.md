`schur_elements(H)`

は、ヘッケ代数 `H` のシュール要素のリストを返します。

```julia-repl
julia> H=hecke(complex_reflection_group(4),Pol(:q))
hecke(G₄,q)

julia> s=schur_elements(H)
7-element Vector{Pol{Cyc{Int64}}}:
 q⁸+2q⁷+3q⁶+4q⁵+4q⁴+4q³+3q²+2q+1
 2√-3+(6+4√-3)q⁻¹+12q⁻²+(6-4√-3)q⁻³-2√-3q⁻⁴
 -2√-3+(6-4√-3)q⁻¹+12q⁻²+(6+4√-3)q⁻³+2√-3q⁻⁴
 2+2q⁻¹+4q⁻²+2q⁻³+2q⁻⁴
 ζ₃²√-3q³+(3-√-3)q²+3q+3+√-3-ζ₃√-3q⁻¹
 -ζ₃√-3q³+(3+√-3)q²+3q+3-√-3+ζ₃²√-3q⁻¹
 q²+2q+2+2q⁻¹+q⁻²

julia> CycPol.(s)
7-element Vector{CycPol{Cyc{Int64}}}:
 Φ₂²Φ₃Φ₄Φ₆
 2√-3q⁻⁴Φ₂²Φ′₃Φ′₆
 -2√-3q⁻⁴Φ₂²Φ″₃Φ″₆
 2q⁻⁴Φ₃Φ₄
 ζ₃²√-3q⁻¹Φ₂²Φ′₃Φ″₆
 -ζ₃√-3q⁻¹Φ₂²Φ″₃Φ′₆
 q⁻²Φ₂²Φ₄
```
