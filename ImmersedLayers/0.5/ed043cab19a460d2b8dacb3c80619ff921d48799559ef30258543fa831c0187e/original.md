```
w_cross_v!(vw::Edges{Primal},w::Nodes{Dual},v::Edges{Primal},base_cache::BasicILMCache,extra_cache::RotConvectiveDerivativeCache)
```

Compute the term `w \times v`, with vorticity `w` and velocity `v`, and return the result in `vw`. This version of the method uses `extra_cache` of type [`RotConvectiveDerivativeCache`](@ref).
