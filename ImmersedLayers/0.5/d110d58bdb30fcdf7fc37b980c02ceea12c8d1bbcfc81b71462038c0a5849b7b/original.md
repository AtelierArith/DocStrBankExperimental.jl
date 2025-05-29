```
convective_derivative!(vdw::Nodes{Dual},v::Edges,w::Nodes{Dual},base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

Compute the convective derivative of `w` with velocity `v`, i.e., $v\cdot \nabla w$, and return the result in `vdw`. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`. This version of the method uses `extra_cache` of type [`ConvectiveDerivativeCache`](@ref).
