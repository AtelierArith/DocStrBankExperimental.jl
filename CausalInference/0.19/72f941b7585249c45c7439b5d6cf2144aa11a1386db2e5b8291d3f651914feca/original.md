```
find_covariate_adjustment(g, X, Y, I = Set{eltype(g)}(), R = setdiff(Set(vertices(g)), X, Y))
```

Find a covariate adjustment set `Z` with $I ⊆ Z ⊆ R$ for sets of vertices `X` and `Y` in `g`, else return `false`. 

Based on the algorithmic approach proposed in https://arxiv.org/abs/1803.00116. 
