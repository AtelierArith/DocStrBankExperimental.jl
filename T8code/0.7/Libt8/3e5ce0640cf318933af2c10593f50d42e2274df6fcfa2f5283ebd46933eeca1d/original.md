```
t8_cmesh_translate_coordinates(coords_in, coords_out, num_vertices, translate)
```

Compute y = x + translate on an array of doubles, interpreting  each 3 as one vector x

# Arguments

  * `coords_in`:[in] The incoming coordinates of the vectors
  * `coords_out`:[out] The computed coordinates of the vectors
  * `num_vertices`:[in] The number of vertices/vectors
  * `translate`:[in] Translation of the vectors.

### Prototype

```c
void t8_cmesh_translate_coordinates (const double *coords_in, double *coords_out, const int num_vertices, const double translate[3]);
```
