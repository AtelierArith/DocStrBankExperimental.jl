```
glb(N1, N2, ...)
```

Given nodes `N1`, `N2`, ... , construct a node `N` with the behaviour `N() = (N1(), N2(), ...)`. That is, `glb` is `tuple` overloaded for nodes.

Equivalent to `@tuple N1 N2 ...`
