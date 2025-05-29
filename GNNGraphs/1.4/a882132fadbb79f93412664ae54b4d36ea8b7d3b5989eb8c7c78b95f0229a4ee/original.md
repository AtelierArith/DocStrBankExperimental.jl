```
sort_edge_index(ei::Tuple) -> u', v'
sort_edge_index(u, v) -> u', v'
```

Return a sorted version of the tuple of vectors `ei = (u, v)`, applying a common permutation to `u` and `v`. The sorting is lexycographic, that is the pairs `(ui, vi)`  are sorted first according to the `ui` and then according to `vi`. 
