```
get_optimal_rotation_matrix(v1s, v2s)
```

Get the `3` x `3` rotation matrix rotating the directions of v1s into v2s. Uses the Kabsch algorithm.

Reference: https://en.wikipedia.org/wiki/Kabsch_algorithm

**Arguments:**

  * `v1s`: `N` x `3` matrix for first  set of 3D points
  * `v2s`: `N` x `3` matrix for second set of 3D points

**Returns:**

  * `R`: 3D matrix rotatating v1s into v2s' directions
