```
find_dsep(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y), veto = no_veto)
```

Find a d-separator `Z` with $I ⊆ Z ⊆ R$ for sets of vertices `X` and `Y` in `g`, else return `false`. 

Based on the algorithmic approach proposed in https://arxiv.org/abs/1803.00116. 
