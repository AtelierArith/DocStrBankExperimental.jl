```
AverageGradient(; kwargs...)
AverageGradient(M::AbstractManifold; kwargs...)
```

勾配プロセッサに勾配の平均を追加します。以前の方向のセット（内部プロセッサからの）と最後の反復が保存され、現在の反復の接空間にベクトル輸送された後に平均が取られます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$（オプション）

# キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `direction=`[`IdentityUpdateRule`](@ref) 実際の勾配にモーメンタムを追加する前に前処理
  * `gradients=[zero_vector(M, p) for _ in 1:n]` 内部ストレージを初期化する方法
  * `n=10` 平均を取るための勾配評価の数
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

!!! info
    この関数は[`AverageGradientRule`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。

