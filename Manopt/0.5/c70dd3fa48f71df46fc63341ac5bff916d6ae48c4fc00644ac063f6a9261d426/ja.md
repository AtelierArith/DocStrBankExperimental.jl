```
QuasiNewtonMatrixDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

`QuasiNewtonMatrixDirectionUpdate`は、演算子が行列として保存される準ニュートン更新ルールを表します。ヘッセ行列の近似の更新、$H_k \mapsto H_{k+1}$、とヘッセ行列の逆行列の近似の更新、$B_k \mapsto B_{k+1}$、の間に区別がなされます。最初のケースでは、基底$\{b_i\}_{i=1}^{n}$に関する探索方向の座標$η_k$は、線形方程式系を解くことによって決定されます。

$$
\text{Solve} \quad \hat{η_k} = - H_k \widehat{\operatorname{grad}f(x_k)},
$$

ここで、$H_k$は基底$\{b_i\}_{i=1}^{n}$に関する演算子を表す行列であり、$\widehat{\operatorname{grad}} f(p_k)$は基底$\{b_i\}_{i=1}^{n}$に関する$x_k$での目的関数$f$の勾配の座標を表します。ヘッセ行列の逆行列が近似される方法が選択される場合、基底$\{b_i\}_{i=1}^{n}$に関する探索方向の座標$η_k$は、単に行列-ベクトルの積によって得られます。

$$
\hat{η_k} = - B_k \widehat{\operatorname{grad}f(x_k)},
$$

ここで、$B_k$は基底$\{b_i\}_{i=1}^{n}$に関する演算子を表す行列であり、$\widehat{\operatorname{grad}} f(p_k)$です。最終的に、探索方向$η_k$は、両方のバリアントにおいて座標$\hat{eta_k}$と基底のベクトル$\{b_i\}_{i=1}^{n}$から生成されます。[`AbstractQuasiNewtonUpdateRule`](@ref)は、どの準ニュートン更新ルールが使用されているかを示します。すべてのルールにおいて、ユークリッド更新式が使用されて行列$H_{k+1}$と$B_{k+1}$が生成され、基底$\{b_i\}_{i=1}^{n}$は、好ましくは等長ベクトル輸送を用いて、次の接空間$T_{p_{k+1}} \mathcal M$に輸送されるか、そこで生成されます。

# 提供されるファンクタ

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` 更新方向を計算する
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` `η`のインプレースで更新方向を計算する

# フィールド

  * `basis`:                  接空間で使用する`AbstractBasis`
  * `matrix`:                 近似演算子を表す行列。
  * `initial_scale`:          更新を初期化する際に、単位行列が初期近似として使用され、この因子でスケーリングされる
  * `update`:                 [`AbstractQuasiNewtonUpdateRule`](@ref)。
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

# コンストラクタ

```
QuasiNewtonMatrixDirectionUpdate(
    M::AbstractManifold,
    update,
    basis::B=default_basis(M),
    m=Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M));
    kwargs...
)
```

## キーワード引数

  * `initial_scale=1.0` – これは`nothing`を渡すことで無効にすることもできます。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

マニフォールドからのデフォルトを使用して更新ルールを生成し、フィールドに対応する名前を付けます。

# 参照

[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref)、[`QuasiNewtonCautiousDirectionUpdate`](@ref)、[`AbstractQuasiNewtonDirectionUpdate`](@ref)、
