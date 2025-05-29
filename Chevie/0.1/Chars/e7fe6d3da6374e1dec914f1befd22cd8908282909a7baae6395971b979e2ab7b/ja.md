`conjPerm(W)`

グループ `W` の文字の順列を返します。これは、文字表の複素共役を取るときに影響を受けます。

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> conjPerm(W)
(2,3)(5,6)
```
