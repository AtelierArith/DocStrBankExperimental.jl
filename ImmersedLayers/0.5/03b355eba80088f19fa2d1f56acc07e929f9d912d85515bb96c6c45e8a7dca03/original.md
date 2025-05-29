```
curl!(w::Nodes{Dual},v::Edges{Primal},cache::BasicILMCache)
curl!(w::Nodes{Dual},v::Edges{Primal},sys::ILMSystem)
```

Compute the discrete curl of `v` and return it in `w`, scaling it by the grid spacing if `cache` (or `sys`) is of `GridScaling` type, or leaving it as a simple differencing if `cache` (or `sys`) is of `IndexScaling` type.
