```
z1 ∧ z2
and(z1,...,zn)
and([z1,...,zn])
```

Returns the logical AND of two or more variables. Use dot broadcasting for vector-valued and matrix-valued Boolean expressions.

```julia
@satvariable(z1[1:n], Bool)
@satvariable(z2[n, 1:m], Bool)
z1 .∧ z2
and.(z1, z2) # equivalent to z1 .∧ z2
```

Special cases:

  * `and(z)` returns `z`.
  * `and(z, false)` returns `false`.
  * `and(z, true)` returns `z`.
