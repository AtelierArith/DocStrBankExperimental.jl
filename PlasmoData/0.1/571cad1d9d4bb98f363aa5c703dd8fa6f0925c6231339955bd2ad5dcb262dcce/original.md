```
symmetric_matrix_to_graph(matrix; attribute="weight", tol = 1e-9)
```

Constructs a `DataGraph` object from a symmetric matrix and saves the values of the matrix to their corresponding edges. The resulting graph is fully connected (every node is connected to every node) and the number of nodes is equal to the dimension of the matrix. Matrix values are saved as edge weights under the name `attribute`. `tol` is the tolerance used when testing that the matrix is symmetric.
