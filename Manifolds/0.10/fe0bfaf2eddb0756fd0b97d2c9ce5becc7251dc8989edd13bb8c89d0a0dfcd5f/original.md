```
manifold_dimension(N::GraphManifold{G,𝔽,M,VertexManifold})
```

returns the manifold dimension of the [`GraphManifold`](@ref) `N` on the vertices of a graph $G=(V,E)$, i.e.

$$
\dim(\mathcal N) = \lvert V \rvert \dim(\mathcal M),
$$

where $\mathcal M$ is the manifold of the data on the nodes.
