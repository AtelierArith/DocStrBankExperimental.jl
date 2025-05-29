```
adjacency_matrix(o::CausalTable)
```

Generate the adjacency matrix induced by the `summaries` and `arrays` attributes of a `CausalTable` object. This matrix denotes which units are *causally dependent* upon one another: an entry of 1 in cell (i,j) indicates that some variable in unit i exhibits a causal relationship to some variable in unit j. 

# Arguments

  * `o::CausalTable`: The `CausalTable` object for which the adjacency matrix is to be generated.

# Returns

A boolean matrix representing the adjacency relationships in the `CausalTable`.
