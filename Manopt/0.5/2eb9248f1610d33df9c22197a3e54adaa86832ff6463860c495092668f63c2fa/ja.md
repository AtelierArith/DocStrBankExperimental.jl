```
AlternatingGradient(; kwargs...)
AlternatingGradient(M::AbstractManifold; kwargs...)
```

勾配に基づく手法が勾配の一部のみを更新することで交互勾配降下を行うべきであることを指定します。

# キーワード引数

  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ の点 $p$ における接ベクトル
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点

!!! info
    この関数は [`AlternatingGradientRule`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。


```
