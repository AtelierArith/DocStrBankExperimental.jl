```
T8codeMesh(ndims, ntrees, nelements, tree_node_coordinates, nodes,
           boundary_names, treeIDs, neighIDs, faces, duals,
           orientations, levels, num_elements_per_tree)
```

Constructor for the `T8codeMesh`. Typically called by the `load_mesh` routine. 

# Arguments

  * `ndims`: Dimension of the mesh.
  * `ntrees`: Global number of trees.
  * `nelements`: Global number of elements.
  * `tree_node_coordinates`: Node coordinates for each tree: [dimension, i, j, k, tree]
  * `nodes`: Array of interpolation nodes.
  * `boundary_names`: List of boundary names.
  * `treeIDs`: List of tree IDs. The length is the number of conforming interfaces of the coarse mesh.
  * `neighIDs`: List of neighboring tree IDs. Same length as `treeIDs`.
  * `faces`: List of face IDs. Same length as `treeIDs`.
  * `duals`: List of face IDs of the neighboring tree. Same length as `treeIDs`.
  * `orientations`: Orientation number of the interface. Same length as `treeIDs`.
  * `levels`: List of levels of each element. Has length `nelements`.
  * `num_elements_per_tree`: List of global number of elements per tree. Has length `ntrees`.

Returns a `T8codeMesh` object with a forest reconstructed by the input arguments.
