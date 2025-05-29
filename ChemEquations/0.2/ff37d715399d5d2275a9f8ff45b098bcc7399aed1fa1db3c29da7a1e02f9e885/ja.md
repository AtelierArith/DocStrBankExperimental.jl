```julia
balance(
    equation::ChemEquations.ChemEquation
) -> Union{ChemEquations.ChemEquation{Rational}, ChemEquations.ChemEquation{T} where T<:Integer}

```

化学反応式の係数をバランスします。反応式がバランスできない場合は、エラーがスローされます。

!!! info
    元の反応式は変更されません。


# 例

```jldoctest
julia> balance(ce"Fe + Cl2 = FeCl3")
2 Fe + 3 Cl2 = 2 FeCl3

julia> balance(ChemEquation{Rational}("H2 + Cl2 = HCl"))
1//2 H2 + 1//2 Cl2 = HCl
```
