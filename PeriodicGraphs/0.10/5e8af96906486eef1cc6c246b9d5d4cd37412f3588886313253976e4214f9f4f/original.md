```
SimpleSymmetry(map::T, dict::D) where {T,D}
```

Create a `SimpleSymmetry{keytype(D),T,D}` object `symm` such that `symm[x]` is

  * `map[dict[x]]` if `x isa keytype(D)`.
  * `map[x]` otherwise, if `x isa Integer`.
