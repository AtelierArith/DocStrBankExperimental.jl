```
z1 ∨ z2
or(z1,...,zn)
or([z1,...,zn])
```

Returns the logical OR of two or more variables. Use dot broadcasting for vector-valued and matrix-valued Boolean expressions.

```julia
@satvariable(z1[1:n], Bool)
@satvariable(z2[1:m, 1:n], Bool)
z1 .∨ z2
or.(z1, z2) # equivalent to z1 .∨ z2
```

Special cases:

  * `or(z)` returns `z`.
  * `or(z, false)` returns `z`.
  * `or(z, true)` returns `true`.

**Note that ∨ (`\vee`) is NOT the ASCII character v.**
