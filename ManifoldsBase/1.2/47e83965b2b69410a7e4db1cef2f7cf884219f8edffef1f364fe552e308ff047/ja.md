```
vector_transport_direction(M::AbstractManifold, p, X, d)
vector_transport_direction(M::AbstractManifold, p, X, d, m::AbstractVectorTransportMethod)
```

与えられた[`AbstractManifold`](@ref) $\mathcal M$において、ベクトル輸送は異なる接空間からのベクトルを識別する[`parallel_transport_direction`](@ref)の一般化です。

より正確には、[AbsilMahonySepulchre:2008](@cite)の定義8.1.1を使用すると、ベクトル輸送 $T_{p,d}: T_p\mathcal M \to T_q\mathcal M$、$p∈ \mathcal M$、$Y∈ T_p\mathcal M$ は、再traction $\operatorname{retr}_p(Y) = q$ に関連する滑らかな写像です。このとき、

1. （関連する再traction）$\mathcal T_{p,d}X ∈ T_q\mathcal M$ であるのは、$q = \operatorname{retr}_p(d)$ の場合に限ります。
2. （一貫性）$\mathcal T_{p,0_p}X = X$ すべての $X∈T_p\mathcal M$ に対して
3. （線形性）$\mathcal T_{p,d}(αX+βY) = α\mathcal T_{p,d}X + β\mathcal T_{p,d}Y$

[`AbstractVectorTransportMethod`](@ref)の場合、3番目のポイントを省略することもできます。[`AbstractLinearVectorTransportMethod`](@ref)は線形です。

# 入力パラメータ

  * `M` マンifold
  * `p` 接空間を示す
  * `X` 輸送される接ベクトル
  * `d` 輸送方向（およびその長さによる距離）を示す
  * `m` [`AbstractVectorTransportMethod`](@ref)、デフォルトは[`default_vector_transport_method`](@ref)、通常は[`ParallelTransport`](@ref)

通常、このメソッドは[`AbstractRetractionMethod`](@ref)も必要です。デフォルトでは、これは[`default_retraction_method`](@ref)であると仮定されるか、ベクトル輸送のために暗黙的に与えられ（および文書化され）ます。ベクトル輸送のために異なる再tractionを明示的に区別するには、[`VectorTransportDirection`](@ref)を参照してください。

開始方向 `d` を指定する代わりに、ターゲット接空間 $T_q\mathcal M$ を同等に指定することもできます。詳細は[`vector_transport_to`](@ref)を参照してください。デフォルトでは[`vector_transport_direction`](@ref)は[`vector_transport_to`](@ref)を使用し、`M`上で[`default_retraction_method`](@ref)を使用します。 ```
