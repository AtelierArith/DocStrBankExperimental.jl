```
polyxor(pgon1::AbstractVector{Point}, pgon2::AbstractVector{Point})
```

Find polygon areas that are inside either `pg1` or `pg2`, but not both.

Return an array of polygons.

Boolean XOR.

Possibly returns holes but does not classify them as holes.
