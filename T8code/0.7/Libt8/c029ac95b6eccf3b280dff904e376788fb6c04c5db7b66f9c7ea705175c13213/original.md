```
t8_geom_get_ref_intersection(edge_index, ref_coords, ref_intersection)
```

Calculates a point of intersection in a triangular reference space. The intersection is the extension of a straight line passing through a reference point and the opposite vertex of the edge. /|\ / | \ o -> reference point / o \ x -> intersection point / | \ /____x____


# Arguments

  * `edge_index`:[in] Index of the edge, the intersection lies on.
  * `ref_coords`:[in] Array containing the coordinates of the reference point.
  * `ref_intersection`:[out] Coordinates of the intersection point.

### Prototype

```c
void t8_geom_get_ref_intersection (int edge_index, const double *ref_coords, double ref_intersection[2]);
```
