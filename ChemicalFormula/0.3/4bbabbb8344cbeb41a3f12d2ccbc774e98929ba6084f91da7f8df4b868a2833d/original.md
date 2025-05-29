```
Formula(formula[, composition][, charge], name=nothing)
```

Represent a chemical `formula` with an electrical `charge` and an optional `name`. The `composition` is automatically determined from the specified `formula`. Compounds can be grouped with parentheses, coordinating molecules can be annotated with a *. Elements are represented by `Symbol`s. If the `charge` is not specified, it is determined from the charge in superscript  within the `formula`. Defaults to 0.

# Examples

```julia-repl
julia> Formula("H2O", "water")
Formula("H2O", Dict{Symbol, Int32}(:H => 2, :O => 1), 0, "water")
julia> Formula("SO4", -2)
Formula("SO4", Dict{Symbol, Int32}(:S => 1, :O => 4), -2, nothing)
julia> Formula("Fe(CN)6*5H2O")
Formula("Fe(CN)6*5H2O", Dict{Symbol, Int32}(:N => 6, :Fe => 1, :H => 10, :O => 5, :C => 6), 0, nothing)
julia> Formula("SO₄²⁻")
Formula("SO₄²⁻", Dict{Symbol, Int32}(:S => 1, :O => 4), -2, nothing)
```
