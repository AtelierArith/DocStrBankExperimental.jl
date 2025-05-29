```
convective_derivative!(vdv::Edges,v::Edges,base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

Compute the convective derivative of `v`, i.e., $v\cdot \nabla v$, and return the result in `vdv`. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`. This version of the method uses `extra_cache` of type [`ConvectiveDerivativeCache`](@ref).
