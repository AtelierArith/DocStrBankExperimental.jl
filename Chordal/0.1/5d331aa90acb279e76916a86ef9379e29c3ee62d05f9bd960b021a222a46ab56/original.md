```
make_selectors_from_cliques(cliques, n)
```

Builds selector matrices `Tℓ` from `cliques`, a list of the cliques in a graph with `n` vertices.

`Tℓ*X*Tℓ'` is the submatrix of `X` corresponding to clique `ℓ`.
