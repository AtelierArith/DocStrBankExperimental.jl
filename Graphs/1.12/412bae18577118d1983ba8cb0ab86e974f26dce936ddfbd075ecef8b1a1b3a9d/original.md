```
steiner_tree(g, term_vert, distmx=weights(g))
```

Return an approximately minimum steiner tree of connected, undirected graph `g` with positive edge  weights represented by `distmx` using [Approximate Steiner Tree](https://en.wikipedia.org/wiki/Steiner_tree_problem#Approximating_the_Steiner_tree).  The minimum steiner tree problem involves finding a subset of edges in `g` of minimum weight such that all the vertices in `term_vert` are connected.

`t = length(term_vert)`.

### Performance

Runtime: O(t*(t*log(t)+|E|*log(|V| )) Memory: O(t*|V|) Approximation Factor: 2-2/t
