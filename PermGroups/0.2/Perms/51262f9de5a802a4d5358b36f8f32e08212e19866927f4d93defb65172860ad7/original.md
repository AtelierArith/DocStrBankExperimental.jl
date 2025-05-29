`Perm{T}(m::AbstractMatrix)` If  `m` is a  permutation matrix, returns  the corresponding permutation of type `T`. If omitted, `T` is taken to be `Int16`.

```julia-repl
julia> Perm([0 1 0;0 0 1;1 0 0])
(1,2,3)
```
