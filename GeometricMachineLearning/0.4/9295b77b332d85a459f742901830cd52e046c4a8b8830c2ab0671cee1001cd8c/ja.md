```
StiefelManifold <: Manifold
```

Stiefel多様体の実装 [hairer2006geometric](@cite)。Stiefel多様体は、すべての列が直交正規である行列 $Y\in\mathbb{R}^{N\times{}n}$ の集合です。すなわち、

$$
    St(n, N) = \{Y: Y^TY = \mathbb{I}_n \}.
$$

Stiefel多様体は、その名前が示すように多様体構造を持つことが示されており、これは`GeometricMachineLearning`で広く使用されています。さらに、これはコンパクトな空間です。詳細は、[`rgrad(::StiefelManifold, ::AbstractMatrix)`](@ref) および [`metric(::StiefelManifold, ::AbstractMatrix, ::AbstractMatrix)`](@ref) のドキュメントストリングで確認できます。
