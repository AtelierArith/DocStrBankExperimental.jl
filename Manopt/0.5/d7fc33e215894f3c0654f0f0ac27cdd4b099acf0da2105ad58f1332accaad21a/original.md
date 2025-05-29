```
AbstractMeshSearchFunction
```

Should be callable as `search!(problem, mesh_size, p, X; kwargs...)`

where `X` is the last successful poll direction from the tangent space at `p` if that exists and the zero vector otherwise.

Besides that the following functions should be implemented

  * `is_successful(search!)` that indicates whether the last search was successful in finding a new candidate
  * `get_candidate(search!)` that returns the last found candidate
