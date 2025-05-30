```
find_frontdoor_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

Find a frontdoor adjustment set `Z` with $I ⊆ Z ⊆ R$ for sets of vertices `X` and `Y` in `g`, else return `false`. 

Based on the algorithm given in  https://arxiv.org/abs/2211.16468. 
