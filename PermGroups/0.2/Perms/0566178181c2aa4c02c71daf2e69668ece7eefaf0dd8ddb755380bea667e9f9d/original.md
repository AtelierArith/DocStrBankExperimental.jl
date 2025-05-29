`struct Perm{T<:Integer}`

A  Perm represents a permutation  of the set `1:n`  and is implemented by a `struct`  with one field,  a `Vector{T}` holding  the images of `1:n`. When showing  a `Perm` at the REPL, the cycle decomposition is displayed as well as the type if it is not `Int16`. The default constructor checks the input, unless the keyword argument `check=false` is given.

```julia-repl
julia> Perms.Perm_(UInt8[1,3,2,4])
Perm{UInt8}: (2,3)
```
