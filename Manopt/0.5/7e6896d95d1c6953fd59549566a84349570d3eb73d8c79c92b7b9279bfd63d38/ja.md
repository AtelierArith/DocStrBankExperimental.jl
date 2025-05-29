```
FletcherReevesCoefficient()
FletcherReevesCoefficient(M::AbstractManifold)
```

[`conjugate_gradient_descent`](@ref) アルゴリズムのための更新係数を [FletcherReeves:1964](@cite) に基づいて計算します。これは多様体に適応されています。

最後の反復と勾配を $p_k,X_k$、現在の反復と勾配を $p_{k+1}, X_{k+1}$、最後の更新方向を $δ_k$ とします。

すると、係数は次のように表されます。

$$
β_k =
\frac{\lVert X_{k+1} \rVert_{p_{k+1}}^2}{\lVert X_k \rVert_{p_{k}}^2}.
$$

!!! info
    この関数は [`FletcherReevesCoefficientRule`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値については、このファクトリは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。

