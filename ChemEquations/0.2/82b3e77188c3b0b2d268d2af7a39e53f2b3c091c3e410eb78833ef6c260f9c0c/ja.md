与えられた文字列から化学反応式を構築します。`{Type}`が提供されていない場合、デフォルトは`Int`です。

解析は空白に対して大文字と小文字を区別しません。[`EQUALCHARS`](@ref)のいずれかの文字は、反応式を二つの側に分け、`+`は反応式を化合物に分けます。

# 例

```jldoctest
julia> ChemEquation("N2+O2⇌2NO")
N2 + O2 = 2 NO

julia> ChemEquation("CH3COOH + Na → H2 + CH3COONa")
C2H4O2 + Na = H2 + C2H3O2Na

julia> ChemEquation("⏣H + Cl2 = ⏣Cl + HCl")
⏣H + Cl2 = ⏣Cl + HCl

julia> ChemEquation{Rational}("1//2 H2 → H")
1//2 H2 = H

julia> ChemEquation{Float64}("0.5 H2 + 0.5 Cl2 = HCl")
0.5 H2 + 0.5 Cl2 = HCl
```
