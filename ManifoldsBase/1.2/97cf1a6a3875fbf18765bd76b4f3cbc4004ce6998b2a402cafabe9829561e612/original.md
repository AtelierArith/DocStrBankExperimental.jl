```
copyto!(M::PowerManifoldNested, Y, p, X)
```

Copy the values elementwise, i.e. call `copyto!(M.manifold, B, a, A)` for all elements `A`, `a` and `B` of `X`, `p`, and `Y`, respectively.
