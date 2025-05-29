```
convective_derivative(v::Edges,base_cache::BasicILMCache)
```

Compute the convective derivative of `v`, i.e., $v\cdot \nabla v$. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`.
