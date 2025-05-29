```
tensorproduct!(q::EdgeGradient,u::Edges,v::Edges,ut::EdgeGradient,vt::EdgeGradient)
```

In-place tensor product of `u` and `v`, with the result returned in `q`. The `ut` and `vt` are supplied as temporary storage.
