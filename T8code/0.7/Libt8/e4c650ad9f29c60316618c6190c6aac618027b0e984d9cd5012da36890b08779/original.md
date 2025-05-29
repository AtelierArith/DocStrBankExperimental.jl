```
t8_triangle_point_inside(p_0, v, w, point, tolerance)
```

Check if a point is inside of a triangle described by a point *p_0* and two vectors *v* and *w*.

# Arguments

  * `p_0`:[in] The first vertex of a triangle
  * `v`:[in] The vector from p_0 to p_1 (second vertex in the triangle)
  * `w`:[in] The vector from p_0 to p_2 (third vertex in the triangle)
  * `point`:[in] The coordinates of the point to check
  * `tolerance`:[in] A double > 0 defining the tolerance

# Returns

0 if the point is outside, 1 otherwise.

### Prototype

```c
int t8_triangle_point_inside (const double p_0[3], const double v[3], const double w[3], const double point[3], const double tolerance);
```
