```
grad!(v::EdgeGradient{Primal/Dual,Dual/Primal},p::Edges{Primal/Dual},cache::BasicILMCache)
grad!(v::EdgeGradient{Primal/Dual,Dual/Primal},p::Edges{Primal/Dual},sys::ILMSystem)
```

Compute the discrete gradient of edge data `p` and return it in `v`, scaling it by the grid spacing if `cache` (or `sys`) is of `GridScaling` type, or leaving it as a simple differencing if `cache` (or `sys`) is of `IndexScaling` type.
