```
t8_geom_get_triangle_scaling_factor(edge_index, tree_vertices, glob_intersection, glob_ref_point)
```

Calculates the scaling factor for edge displacement along a triangular tree face depending on the position of the global reference point.

# Arguments

  * `edge_index`:[in] Index of the edge, whose displacement should be scaled.
  * `tree_vertices`:[in] Array with the tree vertex coordinates.
  * `glob_intersection`:[in] Array containing the coordinates of the intersection point of a line drawn from the opposite vertex through the glob_ref_point onto the edge with edge_index.
  * `glob_ref_point`:[in] Array containing the coordinates of the reference point mapped into the global space.

### Prototype

```c
double t8_geom_get_triangle_scaling_factor (int edge_index, const double *tree_vertices, const double *glob_intersection, const double *glob_ref_point);
```
