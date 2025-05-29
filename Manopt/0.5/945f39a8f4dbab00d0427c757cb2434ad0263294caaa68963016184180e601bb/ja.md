```
MomentumGradient()
```

勾配プロセッサにモーメントを追加し、最後の方向と最後の反復を保存し、新しいものは $η_i = m*η_{i-1}' - s d_i$ として構成されます。ここで、$sd_i$ は現在の（内部の）方向であり、$η_{i-1}'$ はモーメント $m$ で乗算された最後の方向を輸送したベクトルです。

# 入力

  * `M`（オプション）

# キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 多様体 $\mathcal M$ 上の点
  * `direction=`[`IdentityUpdateRule`](@ref) 実際の勾配にモーメントを追加する前に前処理
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `momentum=0.2` 使用するモーメントの量
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照

!!! info
    この関数は [`MomentumGradientRule`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。

