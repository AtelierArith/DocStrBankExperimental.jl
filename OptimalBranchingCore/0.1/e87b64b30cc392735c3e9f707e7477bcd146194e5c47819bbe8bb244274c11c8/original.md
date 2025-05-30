```
covered_by(a::Integer, clause_or_dnf)
```

Check if `a` is covered by the logic expression `clause_or_dnf`.

### Arguments

  * `a`: A bit string.
  * `clause_or_dnf`: Logic expression, which can be a [`Clause`](@ref) object or a [`DNF`](@ref) object.

### Returns

`true` if `a` satisfies `clause_or_dnf`, `false` otherwise.
