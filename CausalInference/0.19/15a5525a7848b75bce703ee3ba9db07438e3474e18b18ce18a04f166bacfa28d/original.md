```
find_backdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

Find a backdoor adjustment set `Z` with $I ⊆ Z ⊆ R$ for sets of vertices `X` and `Y` in `g`, else return `false`. 

The generalization to sets X and Y differs from, e.g., Pearl (2009). See the Example section (TODO: ref).
