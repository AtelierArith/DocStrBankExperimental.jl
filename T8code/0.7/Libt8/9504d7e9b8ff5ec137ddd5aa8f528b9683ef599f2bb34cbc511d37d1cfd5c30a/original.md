```
t8_forest_element_points_inside(forest, ltreeid, element, points, num_points, is_inside, tolerance)
```

Query whether a batch of points lies inside an element. For bilinearly interpolated elements.

!!! note
    For 2D quadrilateral elements this function is only an approximation. It is correct if the four vertices lie in the same plane, but it may produce only approximate results if  the vertices do not lie in the same plane.


# Arguments

  * `forest`:[in] The forest.
  * `ltree_id`:[in] The forest local id of the tree in which the element is.
  * `element`:[in] The element.
  * `points`:[in] 3-dimensional coordinates of the points to check
  * `num_points`:[in] The number of points to check
  * `is_inside`:[in,out] An array of length *num_points*, filled with 0/1 on output. True (non-zero) if a *point*  lies within an *element*, false otherwise. The return value is also true if the point  lies on the element boundary. Thus, this function may return true for different leaf  elements, if they are neighbors and the point lies on the common boundary.
  * `tolerance`:[in] Tolerance that we allow the point to not exactly match the element. If this value is larger we detect more points. If it is zero we probably do not detect points even if they are inside due to rounding errors.

### Prototype

```c
void t8_forest_element_points_inside (t8_forest_t forest, t8_locidx_t ltreeid, const t8_element_t *element, const double *points, int num_points, int *is_inside, const double tolerance);
```
