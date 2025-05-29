```
Polytope{K,M,CRS}
```

We say that a geometry is a K-polytope when it is a collection of "flat" sides that constitute a `K`-dimensional subspace. They are called chain, polygon and polyhedron respectively for 1D (`K=1`), 2D (`K=2`) and 3D (`K=3`) subspaces. The parameter `K` is also known as the rank or parametric dimension of the polytope ([https://en.wikipedia.org/wiki/Abstract_polytope](https://en.wikipedia.org/wiki/Abstract_polytope)).

The term polytope expresses a particular combinatorial structure. A polyhedron, for example, can be decomposed into faces. Each face can then be decomposed into edges, and edges into vertices. Some conventions act as a mapping between vertices and higher dimensional features (edges, faces, cells...), removing the need to store all features.

Additionally, the following property must hold in order for a geometry to be considered a polytope: the boundary of a (K+1)-polytope is a collection of K-polytopes, which may have (K-1)-polytopes in common. See [https://en.wikipedia.org/wiki/Polytope](https://en.wikipedia.org/wiki/Polytope).

### Notes

Type aliases are `Chain`, `Polygon`, `Polyhedron`.
