```
short_vectors_affine(
    S::ZZLat,
    v::QQMatrix,
    alpha::RationalUnion,
    d::RationalUnion
  ) -> Vector{QQMatrix}
```

Given a hyperbolic or negative definite $\mathbb{Z}$-lattice $S$, return the set of vectors

$$
\{x \in S : x^2=d, x.v=\alpha \}.
$$

where $v$ is a given vector in the ambient space of $S$ with positive square, and $\alpha$ and $d$ are rational numbers.

The vectors in output are given in terms of their coordinates in the ambient space of $S$.

The implementation is based on Algorithm 2.2 in [Shi15](@cite)
