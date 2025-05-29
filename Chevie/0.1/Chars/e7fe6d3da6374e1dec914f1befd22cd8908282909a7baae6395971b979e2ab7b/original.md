`conjPerm(W)`

return  the permutation of the characters of the group `W` which is effected when taking the complex conjugate of the character table.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> conjPerm(W)
(2,3)(5,6)
```
