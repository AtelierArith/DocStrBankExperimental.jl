```
QuasiNewtonMatrixDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

`QuasiNewtonMatrixDirectionUpdate`は、演算子が行列として保存される準ニュートン更新ルールを表します。ヘッセ行列の近似の更新、$H_k \mapsto H_{k+1}$、とヘッセ行列の逆行列の近似の更新、$B_k \mapsto B_{k+1}$、の間に区別がなされます。最初のケースでは、基底$\{b_i\}^{n}_{i=1}$に関する探索方向の座標$η_k$は、線形方程式系を解くことによって決定されます。

$$
\text{Solve} \quad \hat{η_k} = - H_k \widehat{\operatorname{grad}f(x_k)},
$$

ここで、$H_k$は基底$\{b_i\}^{n}_{i=1}$に関する演算子を表す行列であり、$\widehat{\operatorname{grad}f(x_k)}$は基底$\{b_i\}^{n}_{i=1}$に関する点$x_k$での目的関数$f$の勾配の座標を表します。ヘッセ行列の逆行列が近似される方法が選択される場合、基底$\{b_i\}^{n}_{i=1}$に関する探索方向の座標$η_k$は、単に行列-ベクトルの積によって得られます。

$$
\hat{η_k} = - B_k \widehat{\operatorname{grad}f(x_k)},
$$

ここで、$B_k$は基底$\{b_i\}^{n}_{i=1}$に関する演算子を表す行列であり、$\widehat{\operatorname{grad}f(x_k)}$です。最終的に、探索方向$η_k$は、両方のバリアントにおいて座標$\hat{eta_k}$と基底のベクトル$\{b_i\}^{n}_{i=1}$から生成されます。[`AbstractQuasiNewtonUpdateRule`](@ref)は、どの準ニュートン更新ルールが使用されているかを示します。すべてのルールにおいて、ユークリッド更新式が使用されて行列$H_{k+1}$と$B_{k+1}$を生成し、基底$\{b_i\}^{n}_{i=1}$は次の接空間$T_{x_{k+1}} \mathcal{M}$に輸送され、好ましくは等距離ベクトル輸送によって、またはそこで生成されます。

# 提供されるファンクタ

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` 更新方向を計算する
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` `η`のインプレースで更新方向を計算する

# フィールド

  * `basis`:                  接空間で使用する`AbstractBasis`
  * `matrix`:                 （`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`）近似演算子を表す行列。
  * `scale`:                  （`true`）最初の行列（=単位行列）が最初の更新前にスケーリングされるべきかどうかを示します。
  * `update`:                 [`AbstractQuasiNewtonUpdateRule`](@ref)。
  * `vector_transport_method`: （`vector_transport_method`）`AbstractVectorTransportMethod`

# コンストラクタ

```
QuasiNewtonMatrixDirectionUpdate(
    M::AbstractManifold,
    update,
    basis::B=DefaultOrthonormalBasis(),
    m=Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M));
    kwargs...
)
```

## キーワード引数

  * `scale`, `vector_transport_method` の2つのフィールドに対して

マニフォールドからデフォルトを使用し、フィールドに対応する名前で更新ルールを生成します。

# 参照

[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
