```
curl!(v::Edges{Primal},s::Nodes{Dual},cache::BasicILMCache)
curl!(v::Edges{Primal},s::Nodes{Dual},sys::ILMSystem)
```

Compute the discrete curl of `s` and return it in `v`, scaling it by the grid spacing if `cache` (or `sys`) is of `GridScaling` type, or leaving it as a simple differencing if `cache` (or `sys`) is of `IndexScaling` type.
