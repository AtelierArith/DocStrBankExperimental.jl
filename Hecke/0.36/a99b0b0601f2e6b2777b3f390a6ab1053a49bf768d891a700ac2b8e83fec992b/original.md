```
primitive_closure(M::AbstractLat, N::AbstractLat) -> AbstractLat
```

Given two lattices `M` and `N` defined over a number field `E`, with $N \subseteq E\otimes M$, return the primitive closure $M \cap E\otimes N$ of `N` in `M`.

One can also use the alias `saturate(L, M)`.
