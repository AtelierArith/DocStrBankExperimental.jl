```
cut_size(g::AbstractGraph, config; weights=UnitWeight(ne(g)))
```

Return the size of the cut of the graph `g` with configuration `config`. The configuration is a vector of boolean numbers as the group indices of vertices. Edges between vertices in different groups are counted as a cut.
