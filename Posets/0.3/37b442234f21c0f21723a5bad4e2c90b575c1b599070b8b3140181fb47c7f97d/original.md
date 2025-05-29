```
comparability_graph(p::Poset)
```

Return the comparability graph of `p`. This is graph in which there is an edge  between `i` and `j` if and only if `p[i] < p[j]` or `p[j] < p[i]`.
