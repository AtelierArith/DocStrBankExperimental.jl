```
incidence_poset(g::AbstractGraph)
```

Given a graph `g` create a poset whose elements correspond to the vertices  and edges of `g` in which the only relations are of the form `v < e` where `v`  is a vertex that is an end point of edge `e`. 
