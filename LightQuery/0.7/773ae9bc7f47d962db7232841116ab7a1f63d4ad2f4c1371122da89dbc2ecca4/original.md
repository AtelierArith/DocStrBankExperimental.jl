```
Enumerate{Unenumerated}
```

"Sees through" most iterators into their `parent`.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred collect(Enumerate(Iterators.filter(iseven, [4, 3, 2, 1])))
2-element Array{Tuple{Int64,Int64},1}:
 (1, 4)
 (3, 2)
```
