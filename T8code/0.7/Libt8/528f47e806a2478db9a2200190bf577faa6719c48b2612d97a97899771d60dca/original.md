```
t8_line_point_inside(p_0, vec, point, tolerance)
```

Check if a point is inside a line that is defined by a starting point *p_0* and a vector *vec*

# Arguments

  * `p_0`:[in] Starting point of the line
  * `vec`:[in] Direction of the line (not normalized)
  * `point`:[in] The coordinates of the point to check
  * `tolerance`:[in] A double > 0 defining the tolerance

# Returns

0 if the point is outside, 1 otherwise.

### Prototype

```c
int t8_line_point_inside (const double *p_0, const double *vec, const double *point, const double tolerance);
```
