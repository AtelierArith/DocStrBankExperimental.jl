```
manifold_dimension(N::GraphManifold{G,𝔽,M,EdgeManifold})
```

returns the manifold dimension of the [`GraphManifold`](@ref) `N` on the edges of a graph $G=(V,E)$, i.e.

$$
\dim(\mathcal N) = \lvert E \rvert \dim(\mathcal M),
$$

where $\mathcal M$ is the manifold of the data on the edges.
