```
t8_geom_get_scaling_factor_of_edge_on_face_tet(edge_index, face_index, ref_coords)
```

Calculates the scaling factor for the displacement of an edge over a face of a tetrahedral element.

# Arguments

  * `edge_index`:[in] Index of the edge, whose displacement should be scaled.
  * `face_index`:[in] Index of the face, the displacement should be scaled on.
  * `ref_coords`:[in] Array containing the coordinates of the reference point.

# Returns

The scaling factor of the edge displacement on the face at the point of the reference coordinates.

### Prototype

```c
double t8_geom_get_scaling_factor_of_edge_on_face_tet (int edge_index, int face_index, const double *ref_coords);
```
