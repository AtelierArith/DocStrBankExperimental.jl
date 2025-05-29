```
t8_cmesh_tree_vertices_negative_volume(eclass, vertices, num_vertices)
```

Given a set of vertex coordinates for a tree of a given eclass. Query whether the geometric volume of the tree with this coordinates would be negative.

# Arguments

  * `eclass`:[in] The eclass of a tree.
  * `vertices`:[in] The coordinates of the tree's vertices.
  * `num_vertices`:[in] The number of vertices. *vertices* must hold 3 * *num_vertices* many doubles. *num_vertices* must match t8*eclass*num_vertices[*eclass*]

# Returns

True if the geometric volume describe by *vertices* is negative. False otherwise. Returns true if a tree of the given eclass with the given vertex coordinates does have negative volume.

### Prototype

```c
int t8_cmesh_tree_vertices_negative_volume (const t8_eclass_t eclass, const double *vertices, const int num_vertices);
```
