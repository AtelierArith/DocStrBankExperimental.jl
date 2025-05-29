```
short_vectors_affine
    gram::MatrixElem{T},
    v::MatrixElem{T},
    alpha::RationalUnion,
    d::RationalUnion
  ) where T <: Union{ZZRingElem, QQFieldElem} -> Vector{MatrixElem{T}}
```

Given the Gram matrix `gram` of a hyperbolic or negative definite $\mathbb{Z}$-lattice $S$, return the set of vectors

$$
\{x \in S : x^2=d, x.v=\alpha \}.
$$

where $v$ is a given vector of positive square, represented by its coordinates in the standard basis of the rational span of $S$, and $\alpha$ and $d$ are rational numbers.

The vectors in output are given in terms of their coordinates in the rational span of $S$.

The implementation is based on Algorithm 2.2 in [Shi15](@cite)
