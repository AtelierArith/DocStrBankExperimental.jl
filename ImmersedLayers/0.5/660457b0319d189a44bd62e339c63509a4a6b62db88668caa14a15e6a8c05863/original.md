```
divergence!(p::Nodes{Primal/Dual},v::Edges{Primal/Dual},cache::BasicILMCache)
divergence!(p::Nodes{Primal/Dual},v::Edges{Primal/Dual},sys::ILMSystem)
```

Compute the discrete divergence of `v` and return it in `p`, scaling it by the grid spacing if `cache` (or `sys`) is of `GridScaling` type, or leaving it as a simple differencing if `cache` (or `sys`) is of `IndexScaling` type.
