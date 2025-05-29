```
function merge_linear_combination(g::AbstractGraph)

Returns a copy of computational graph `g` with multiplicative prefactors factorized,
e.g., 3*g1 + 5*g2 + 7*g1 + 9*g2 ↦ 10*g1 + 14*g2 = linear_combination(g1, g2, 10, 14).
Returns a linear combination of unique subgraphs and their total prefactors. 
Does nothing if the graph `g` does not represent a Sum operation.
```

# Arguments:

  * `g::AbstractGraph`: graph to be modified
