```
convective_derivative(v::Edges{Primal},p::Nodes{Primal},base_cache::BasicILMCache)
```

Compute the convective derivative of `p` with velocity `v`, i.e., $v\cdot \nabla p$. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`.
