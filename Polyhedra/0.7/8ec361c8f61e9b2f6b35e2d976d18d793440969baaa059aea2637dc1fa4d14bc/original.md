```
project(p::Polyhedron, P::AbstractMatrix)
```

Projects the polyhedron `p` into the `size(P, 2)`-dimensional linear subspace spanned by the columns of `P`. The new orthonormal basis for this subspace is computed by applying the Gram–Schmidt process to the columns of `P`, starting with the first column.
