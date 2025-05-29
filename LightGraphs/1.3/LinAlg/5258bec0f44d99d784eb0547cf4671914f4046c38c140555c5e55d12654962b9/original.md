```
Nonbacktracking{G}
```

A compact representation of the nonbacktracking operator.

The Nonbacktracking operator can be used for community detection. This representation is compact in that it uses only ne(g) additional storage and provides an implicit representation of the matrix B_g defined below.

Given two arcs $A_{i j}` and `A_{k l}` in `g`, the non-backtraking matrix$B`` is defined as

$B_{A_{i j}, A_{k l}} = δ_{j k} * (1 - δ_{i l})$

This type is in the style of GraphMatrices.jl and supports the necessary operations for computed eigenvectors and conducting linear solves.

Additionally the `contract!(vertexspace, nbt, edgespace)` method takes vectors represented in the domain of $B$ and represents them in the domain of the adjacency matrix of `g`.
