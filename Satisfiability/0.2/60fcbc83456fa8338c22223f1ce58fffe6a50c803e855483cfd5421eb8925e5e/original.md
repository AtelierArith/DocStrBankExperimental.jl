```
not(z::BoolExpr)
¬z
```

Return the logical negation of `z`.

Note: Broacasting a unary operator requires the syntax `.¬z` which can be confusing to new Julia users. We define `¬(z::Array{BoolExpr})` for convenience.

```julia
    @satvariable(z[1:n], Bool)
    ¬z  # syntactic sugar for map(¬, z)
    .¬z # also valid
```
