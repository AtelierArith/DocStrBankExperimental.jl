```
MultiLevelPoisson{N,M}
```

Composite type used to solve the pressure Poisson equation with a [geometric multigrid](https://en.wikipedia.org/wiki/Multigrid_method) method. The only variable is `levels`, a vector of nested `Poisson` systems.
