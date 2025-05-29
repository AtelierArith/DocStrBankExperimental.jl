@perm"..."

makes a `Perm{Int16}` from a string; allows GAP-style `perm"(1,2)(5,6,7)(4,9)"`. If the cycle decomposition is preceded by `"Perm{T}:"` the constructed  permutation is of type `T`.

```julia-repl
perm"Perm{UInt8}:(1,2)(3,4)"
Perm{UInt8}: (1,2)(3,4)
```
