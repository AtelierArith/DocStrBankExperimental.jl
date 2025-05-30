```
list_backdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

List all back-door adjustment sets `Z` with $I ⊆ Z ⊆ R$ for sets of vertices `X` and `Y` in `g`. 
