```
vertices_list(lm::LinearMap; prune::Bool=true)
```

Return the list of vertices of a (polytopic) linear map.

### Input

  * `lm`    – linear map
  * `prune` – (optional, default: `true`) if `true`, we remove redundant vertices

### Output

A list of vertices.

### Algorithm

We assume that the underlying set `X` is polytopic and compute the vertices of `X`. The result is just the linear map applied to each vertex.
