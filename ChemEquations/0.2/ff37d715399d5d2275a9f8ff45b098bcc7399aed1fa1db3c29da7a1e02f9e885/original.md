```julia
balance(
    equation::ChemEquations.ChemEquation
) -> Union{ChemEquations.ChemEquation{Rational}, ChemEquations.ChemEquation{T} where T<:Integer}

```

Balances the coefficients of a chemical equation. If the equation cannot be balanced, an error is thrown.

!!! info
    The original equation is not modified.


# Examples

```jldoctest
julia> balance(ce"Fe + Cl2 = FeCl3")
2 Fe + 3 Cl2 = 2 FeCl3

julia> balance(ChemEquation{Rational}("H2 + Cl2 = HCl"))
1//2 H2 + 1//2 Cl2 = HCl
```
