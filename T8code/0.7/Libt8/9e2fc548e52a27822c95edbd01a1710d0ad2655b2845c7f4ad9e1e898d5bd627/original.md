```
t8_element_shape_compare(element_shape1, element_shape2)
```

Compare two element_shapees of the same dimension as necessary for face neighbor orientation. The implemented order is Triangle < Square in 2D and Tet < Hex < Prism < Pyramid in 3D.

# Arguments

  * `element_shape1`:[in] The first element_shape to compare.
  * `element_shape2`:[in] The second element_shape to compare.

# Returns

0 if the element_shapees are equal, 1 if element_shape1 > element_shape2 and -1 if element_shape1 < element_shape2

### Prototype

```c
int t8_element_shape_compare (t8_element_shape_t element_shape1, t8_element_shape_t element_shape2);
```
