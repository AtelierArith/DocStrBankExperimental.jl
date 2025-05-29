```
t8_cmesh_coords_axb(coords_in, coords_out, num_vertices, alpha, b)
```

Compute y = ax + b on an array of doubles, interpreting each 3 as one vector x

# Arguments

  * `coords_in`:[in] The incoming coordinates of the vectors
  * `coords_out`:[out] The computed coordinates of the vectors
  * `num_vertices`:[in] The number of vertices/vectors
  * `alpha`:[in] Scaling factor for the vectors
  * `b`:[in] Translation of the vectors.

### Prototype

```c
void t8_cmesh_coords_axb (const double *coords_in, double *coords_out, int num_vertices, double alpha, const double b[3]);
```
