```
integer_lattice(S::Symbol, n::RationalUnion = 1) -> ZZlat
```

Given `S = :H` or `S = :U`, return a $\mathbb Z$-lattice admitting $n*J_2$ as Gram matrix in some basis, where $J_2$ is the 2-by-2 matrix with 0's on the main diagonal and 1's elsewhere.
