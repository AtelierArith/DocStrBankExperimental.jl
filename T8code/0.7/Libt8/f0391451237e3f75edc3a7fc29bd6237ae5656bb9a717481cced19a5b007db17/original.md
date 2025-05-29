```
t8_vertex_point_inside(vertex_coords, point, tolerance)
```

Check if a point lies inside a vertex

# Arguments

  * `vertex_coords`:[in] The coordinates of the vertex
  * `point`:[in] The coordinates of the point to check
  * `tolerance`:[in] A double > 0 defining the tolerance

# Returns

0 if the point is outside, 1 otherwise.

### Prototype

```c
int t8_vertex_point_inside (const double vertex_coords[3], const double point[3], const double tolerance);
```
