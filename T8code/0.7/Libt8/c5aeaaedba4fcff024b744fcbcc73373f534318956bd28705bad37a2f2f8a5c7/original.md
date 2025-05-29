```
t8_geometry_linear_axis_aligned_new()
```

Create a new linear, axis-aligned geometry of a given dimension. The geometry is only viable for line/quad/hex elements and uses two vertices (min and max coords) per tree. The vertices are saved via the t8*cmesh*set*tree*vertices function.

# Returns

A pointer to an allocated t8_geometry_linear_axis_aligned struct, as if the t8_geometry_linear_axis_aligned () constructor was called.

### Prototype

```c
t8_geometry_c * t8_geometry_linear_axis_aligned_new ();
```
