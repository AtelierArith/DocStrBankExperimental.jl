```
convective_derivative!(vdp::Nodes{Primal},v::Edges,p::Nodes{Primal},base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

Compute the convective derivative of `p` with velocity `v`, i.e., $v\cdot \nabla p$, and return the result in `vdp`. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`. This version of the method uses `extra_cache` of type [`ConvectiveDerivativeCache`](@ref).
