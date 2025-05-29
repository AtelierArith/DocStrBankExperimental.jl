```julia
balance(
    equation::ChemEquations.ChemEquation{<:Union{Complex{S}, S} where S<:Integer};
    fractions
) -> Union{ChemEquations.ChemEquation{Rational}, ChemEquations.ChemEquation{T} where T<:Integer}

```

Balances the coefficients of a chemical equation with integer coefficients.

The minimal integer solution is displayed by default. If `fractions` is true, they solution will be displayed as rational fractions instead.

# Examples

```jldoctest
julia> balance(ce"Fe + Cl2 = FeCl3", fractions=true)
Fe + 3//2 Cl2 = FeCl3

julia> balance(ce"Cr2O7{-2} + H{+} + {-} = Cr{+3} + H2O")
Cr2O7{-2} + 14 H{+} + 6 e = 2 Cr{+3} + 7 H2O
```
