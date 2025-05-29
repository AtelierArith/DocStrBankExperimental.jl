`cycles(p::SPerm)` the non-trivial cycles of `p`.

Two cycles which differ only by sign are returned once only.

```julia-repl
julia> cycles(SPerm(-1,2)*SPerm(3,-3)*SPerm(4,5,-4,-5))
3-element Vector{Vector{Int16}}:
 [1, -2]
 [3, -3]
 [4, 5, -4, -5]
```
