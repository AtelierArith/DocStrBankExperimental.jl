`cycles(p::SPerm)` は `p` の非自明なサイクルを返します。

符号のみが異なる2つのサイクルは一度だけ返されます。

```julia-repl
julia> cycles(SPerm(-1,2)*SPerm(3,-3)*SPerm(4,5,-4,-5))
3-element Vector{Vector{Int16}}:
 [1, -2]
 [3, -3]
 [4, 5, -4, -5]
```
