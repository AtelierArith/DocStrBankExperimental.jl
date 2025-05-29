```
dependency_matrix(o::CausalTable)
```

Generate the dependency matrix induced by the `summaries` and `arrays` attributes of a `CausalTable` object. This matrix stores which units are *statistically dependent* upon one another: an entry of 1 in cell (i,j) indicates that the data of unit i is correlated with the data in unit j. Two units are correlated if they either are causally dependent (neighbors in the adjacency matrix) or share a common cause (share a neighbor in the adjacency matrix).

# Arguments

  * `o::CausalTable`: The `CausalTable` object for which the dependency matrix is to be generated.

# Returns

A boolean matrix representing the  relationships in the `CausalTable`.
