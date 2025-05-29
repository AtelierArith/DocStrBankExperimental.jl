```
manifold_dimension(N::GraphManifold{G,𝔽,M,EdgeManifold})
```

は、グラフ $G=(V,E)$ のエッジ上の [`GraphManifold`](@ref) `N` の多様体次元を返します。すなわち、

$$
\dim(\mathcal N) = \lvert E \rvert \dim(\mathcal M),
$$

ここで、$\mathcal M$ はエッジ上のデータの多様体です。
