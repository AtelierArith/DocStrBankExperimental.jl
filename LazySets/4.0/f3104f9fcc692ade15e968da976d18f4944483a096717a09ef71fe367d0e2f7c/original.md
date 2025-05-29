```
vertices_list(ilm::InverseLinearMap; prune::Bool=true)
```

Return the list of vertices of a (polyhedral) inverse linear map.

### Input

  * `ilm`   – inverse linear map
  * `prune` – (optional, default: `true`) if `true`, remove redundant vertices

### Output

A list of vertices.

### Algorithm

We assume that the underlying set `X` is polyhedral. Then the result is just the inverse linear map applied to the vertices of `X`.
