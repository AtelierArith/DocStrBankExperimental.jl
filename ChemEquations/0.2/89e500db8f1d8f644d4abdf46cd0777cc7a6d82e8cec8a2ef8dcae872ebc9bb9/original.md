```julia
Compound(str::AbstractString) -> ChemEquations.Compound

```

Constructs a compound from `str`.

An element begins with an uppercase unicode letter and ends with a lowercase unicode letter or a unicode symbol.

!!! info
    An element can also begin with a symbol if the symbol is the first character (e.g. `"⬡H"`).


Parsing is insensitive to whitespace and underscores (`_`), but also to state symbols (`(s)`, `(l)`, `(g)`, `(aq)`). Special parsing is implemented for:

  * parens (e.g. `"(CH3COO)2Mg"`)
  * compounds with `"*"` (e.g. `"CuSO4 * 5H2O"`)
  * electrons (`"e"`)

Charge is in the form `"{±n}"` or `"{n±}"`. It is automatically deduced for electron (`"e"`).

# Examples

```jldoctest
julia> Compound("H2O(s)")
H2O

julia> Compound("H3O{+}")
H3O{+}

julia> Compound("(CH3COO)2Mg")
C4H6O4Mg

julia> Compound("CuSO4 * 5H2O")
CuSO9H10

julia> Compound("⬡Cl")
⬡Cl
```
