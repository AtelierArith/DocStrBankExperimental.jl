```
manifold_dimension(N::GraphManifold{G,𝔽,M,VertexManifold})
```

は、グラフ $G=(V,E)$ の頂点における [`GraphManifold`](@ref) `N` の多様体次元を返します。すなわち、

$$
\dim(\mathcal N) = \lvert V \rvert \dim(\mathcal M),
$$

ここで、$\mathcal M$ はノード上のデータの多様体です。
