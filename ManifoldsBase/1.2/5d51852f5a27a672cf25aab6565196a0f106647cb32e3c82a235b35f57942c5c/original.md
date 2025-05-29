```
copyto!(M::PowerManifoldNested, q, p)
```

Copy the values elementwise, i.e. call `copyto!(M.manifold, b, a)` for all elements `a` and `b` of `p` and `q`, respectively.
