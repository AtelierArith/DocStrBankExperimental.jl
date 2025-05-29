```
z1 ⟹ z2
implies(z1, z2)
```

Returns the expression z1 IMPLIES z2. Use dot broadcasting for vector-valued and matrix-valued Boolean expressions. Note: `implies(z1, z2)` is equivalent to `or(not(z1), z2)`.
