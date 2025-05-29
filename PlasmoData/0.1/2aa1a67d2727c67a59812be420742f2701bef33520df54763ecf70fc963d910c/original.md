```
matrix_to_graph(matrix; diagonal = true, attribute="weight")
matrix_to_graph(array_3d; diagonal = true, attributes = ["weight$i" for i in 1:size(array_3d)[3]])
```

Constructs a `DataGraph` object from a matrix and saves the matrix data as node attributes under the name `attribute`. If `diagonal = false`, the graph has a mesh structure, where each matrix entry is represented by a node, and each node is connected to the adjacent matrix entries/nodes. If `diagonal = true`, entries of the matrix are also connected to the nodes diagonal to them (i.e., entry (i,j) is connected to (i-1, j-1), (i + 1, j -1), etc.).

If a 3D matrix is passed to the function, it treats the first two dimensions as the matrix and then saves the data in the third dimension as different weights (i.e., for array of size dim1, dim2, and dim3, entry (i,j) has dim3 weights). `attribute_list` can be defined by the user to give names to each weight in the third dimension.
