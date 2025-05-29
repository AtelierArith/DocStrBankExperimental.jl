```
grad!(v::Edges{Primal/Dual},p::Nodes{Primal/Dual},cache::BasicILMCache)
grad!(v::Edges{Primal/Dual},p::Nodes{Primal/Dual},sys::ILMSystem)
```

Compute the discrete gradient of `p` and return it in `v`, scaling it by the grid spacing if `cache` (or `sys`) is of `GridScaling` type, or leaving it as a simple differencing if `cache` (or `sys`) is of `IndexScaling` type.
