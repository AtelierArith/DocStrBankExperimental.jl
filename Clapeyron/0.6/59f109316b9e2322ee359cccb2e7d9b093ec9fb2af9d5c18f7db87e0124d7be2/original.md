```
has_reference_state(model)::Bool
```

Checks if the input `EoSModel` has a reference state. Returns `true/false`

## Examples

```julia-repl
julia> has_reference_state(PCSAFT("water"))
false

julia> has_reference_state(PCSAFT("water",idealmodel = ReidIdeal))
true
```

Note that the default idealmodel (`BasicIdeal`) does not allow for setting reference states.
