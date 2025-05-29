```
LowerTriangularAdaptivePoll <: AbstractMeshPollFunction
```

セクション6および7に基づいてメッシュ（ポールステップ）を生成します [Dreisigmeyer:2007](@cite)、2つの小さな修正を加えます：

  * メッシュはグローバルにスケーリングできるため、$Δ_0^m=1$の代わりに特定の異なるスケールが使用されます
  * ポール方向が長すぎる場合は再スケーリングできます。これは、例えば、単射半径を超えないようにするためです。

# ファンクタ

```
(p::LowerTriangularAdaptivePoll)(problem, mesh_size; scale_mesh=1.0, max_stepsize=inf)
```

# フィールド

  * `base_point::P`: メリフォールド上の点で、接空間にメッシュが構築されます
  * `basis`: メッシュが保存される接空間の基底
  * `candidate::P`: 新しい点/候補のためのメモリ
  * `mesh`: メッシュを保存する接ベクトルのベクトル。
  * `random_vector`: $d$次元のランダムベクトル $b_l$`
  * `random_index`: ランダムインデックス $ι$
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `X::T` 最後に成功したポール方向を接ベクトルとして保存します。ゼロベクトルに初期化され、新しい接空間に移動した後にゼロベクトルにリセットされます。

# コンストラクタ

```
LowerTriangularAdaptivePoll(M, p=rand(M); kwargs...)
```

## キーワード引数

  * `basis=`[`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`)
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: メリフォールド $\mathcal M$ 上の点 $p$ での接ベクトル
