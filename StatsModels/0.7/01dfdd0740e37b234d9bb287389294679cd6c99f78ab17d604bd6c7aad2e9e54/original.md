```
termnames(t::FormulaTerm)
```

Return a two-tuple of `termnames` applied to the left and right hand sides of the formula.

!!! note
    Until `apply_schema` has been called, literal `1` in formulae is interpreted as `ConstantTerm(1)` and will thus appear as `"1"` in the returned term names.


```jldoctest
julia> termnames(@formula(y ~ 1 + x * y + (1+x|g)))
("y", ["1", "x", "y", "x & y", "(1 + x) | g"])
```

Similarly, formulae with an implicit intercept will not have a `"1"` in their variable names, because the implicit intercept does not exist until `apply_schema` is called (and may not exist for certain model contexts).

```jldoctest
julia> termnames(@formula(y ~ x * y + (1+x|g)))
("y", ["x", "y", "x & y", "(1 + x) | g"])
```
