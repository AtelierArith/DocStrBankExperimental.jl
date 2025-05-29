```
interpolate(mesh,vector;n=2^3)
```

Interpolate a vector `vector` of values on a uniform collocation grid defined by `mesh`.

Return `(new_mesh,new_vector)` a new uniform mesh with `n` times as many values, and the vector of values at these collocation points.
