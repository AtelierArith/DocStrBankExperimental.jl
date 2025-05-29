`detPerm(W)`

return  the permutation of the characters of the reflection group `W` which is effected when tensoring by the determinant character (for Coxeter groups this is the sign character).

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> detPerm(W)
(1,8)(2,9)(3,11)(4,13)(7,12)
```
