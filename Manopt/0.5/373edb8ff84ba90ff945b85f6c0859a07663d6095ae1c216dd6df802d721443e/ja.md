```
ConjugateDescentCoefficient()
ConjugateDescentCoefficient(M::AbstractManifold)
```

古典的な共役勾配係数を計算します。これは、[Fletcher:1987](@cite) に基づいており、マニフォールドに適応されています。

最後の反復と勾配を $p_k,X_k$、現在の反復と勾配を $p_{k+1}, X_{k+1}$ とし、最後の更新方向を $δ_k$ とします。

すると、係数は次のように表されます。

$$
β_k = \frac{\lVert X_{k+1} \rVert_{p_{k+1}}^2}{⟨-δ_k,X_k⟩_{p_k}}
$$

!!! info
    この関数は [`ConjugateDescentCoefficientRule`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。マニフォールドに依存するデフォルト値については、このファクトリーは、例えば対応する [`AbstractManoptSolverState`](@ref) からマニフォールドが利用可能になるまで構築を延期します。

