`braid_relations(W)`

this  function returns the  relations which present  the braid group of the reflection group `W`. These are homogeneous (both sides of the same length) relations  between generators in bijection  with the generating reflections of  `W`. A presentation  of `W` is  obtained by adding relations specifying the order of the generators.

```julia-repl
julia> W=complex_reflection_group(29)
G₂₉

julia> braid_relations(W)
7-element Vector{Tuple{Vector{Int64}, Vector{Int64}}}:
 ([1, 2, 1], [2, 1, 2])
 ([2, 4, 2], [4, 2, 4])
 ([3, 4, 3], [4, 3, 4])
 ([2, 3, 2, 3], [3, 2, 3, 2])
 ([1, 3], [3, 1])
 ([1, 4], [4, 1])
 ([4, 3, 2, 4, 3, 2], [3, 2, 4, 3, 2, 4])
```

each  relation  is  represented  as  a  pair  of lists, specifying that the product  of the  generators according  to the  indices on  the left side is equal  to the product according to the  indices on the right side. See also `diagram`.
