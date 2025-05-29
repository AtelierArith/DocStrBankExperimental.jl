```
lll(L::ZZLat, same_ambient::Bool = true) -> ZZLat
```

Given an integral $\mathbb Z$-lattice `L` with basis matrix `B`, compute a basis `C` of `L` such that the gram matrix $G_C$ of `L` with respect to `C` is LLL-reduced.

By default, it creates the lattice in the same ambient space as `L`. This can be disabled by setting `same_ambient = false`. Works with both definite and indefinite lattices.
