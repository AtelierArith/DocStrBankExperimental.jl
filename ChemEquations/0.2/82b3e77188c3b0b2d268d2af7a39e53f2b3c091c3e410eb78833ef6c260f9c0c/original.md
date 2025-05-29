Constructs a chemical equation from the given string. If no `{Type}` is provided, it defaults to `Int`.

Parsing is insensitive to whitespace. Any character in [`EQUALCHARS`](@ref) separates the equation into two sides, while `+` separates the equation into compounds.

# Examples

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

```
