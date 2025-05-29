```
convective_derivative!(vdu::Edges,v::Edges,u::Edges,base_cache::BasicILMCache,extra_cache::ConvectiveDerivativeCache)
```

Compute the convective derivative of `u`, i.e., $v\cdot \nabla u$, and return the result in `vdu`. The result is either divided by unity or the grid cell size depending on whether `base_cache` is of type `IndexScaling` or `GridScaling`. This version of the method uses `extra_cache` of type [`ConvectiveDerivativeCache`](@ref).
