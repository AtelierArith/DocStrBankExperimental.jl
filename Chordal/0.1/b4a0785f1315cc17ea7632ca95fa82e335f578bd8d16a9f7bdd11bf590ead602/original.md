```
make_selectors_from_clique_graph(cg::CliqueGraph, n)
```

Builds selector matrices `Tℓ` from `cg`, a CliqueGraph with `n` vertices.

`Tℓ*X*Tℓ'` is the submatrix of `X` corresponding to clique `ℓ`.
