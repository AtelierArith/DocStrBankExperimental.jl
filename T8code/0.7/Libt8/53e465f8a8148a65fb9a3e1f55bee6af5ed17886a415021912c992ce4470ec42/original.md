```
t8_eclass_count_boundary(theclass, min_dim, per_eclass)
```

Query the element class and count of boundary points.

# Arguments

  * `theclass`:[in] We query a point of this element class.
  * `min_dim`:[in] Ignore boundary points of lesser dimension. The ignored points get a count value of 0.
  * `per_eclass`:[out] Array of length T8_ECLASS_COUNT to be filled with the count of the boundary objects, counted per each of the element classes.

# Returns

The count over all boundary points.

### Prototype

```c
int t8_eclass_count_boundary (t8_eclass_t theclass, int min_dim, int *per_eclass);
```
