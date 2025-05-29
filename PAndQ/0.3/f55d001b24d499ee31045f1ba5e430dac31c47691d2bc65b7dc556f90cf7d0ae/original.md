```
interpret(valuation, p)
```

Substitute each atom in `p` with values given by the `valuation`.

The `valuation` can be a `Function` that accepts an atom and returns a logical value, a `Dict`ionary mapping from atoms to logical values, or an iterable that can construct such a dictionary. No substitution is performed if an atom is not one of the dictionary's keys.

# Examples

```jldoctest
julia> @atomize interpret(atom -> ⊤, ¬p)
¬⊤

julia> @atomize interpret(p => ⊤, p ∧ q)
⊤ ∧ q
```
