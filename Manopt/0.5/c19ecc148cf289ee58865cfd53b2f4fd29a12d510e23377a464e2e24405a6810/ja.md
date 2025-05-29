```
QuasiNewtonLimitedMemoryDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

この [`AbstractQuasiNewtonDirectionUpdate`](@ref) は、近似演算子が $m$ 個の保存された接ベクトルのペア $\{\widehat{s}_i\}_{i=k-m}^{k-1}$ と $\{\widehat{y}_i\}_{i=k-m}^{k-1}$ で表される制限付きメモリリーマンBFGS更新を表します。探索方向 $X_k$ の計算には、二重ループ再帰の一般化が使用されます（[HuangGallivanAbsil:2015](@cite) を参照）。これは、$T_{p_k}\mathcal M$ 内の接ベクトルの内積と線形結合のみを必要とします。そのため、保存された接ベクトルのペア $\widehat{s}_i,  \widehat{y}_i$、目的関数 $f$ の勾配 $\operatorname{grad} f(p_k)$ および正定値自己随伴演算子

$$
\mathcal{B}^{(0)}_k[⋅] = \frac{g_{p_k}(s_{k-1}, y_{k-1})}{g_{p_k}(y_{k-1}, y_{k-1})} \; \mathrm{id}_{T_{p_k} \mathcal{M}}[⋅]
$$

が使用されます。二重ループ再帰は、接ベクトル $\widehat{s}_i,\widehat{y}_i$ を使用して、[`InverseBFGS`](@ref) 更新が $\mathcal B^{(0)}_k[⋅]$ に対して $m$ 回連続して実行されると理解できます。同時に、結果として得られる演算子 $\mathcal B^{LRBFGS}_k [⋅]$ が $\operatorname{grad}f(x_k)$ に直接適用されます。更新時には2つのケースがあります：まだ空きメモリがある場合、$k < m$ のとき、以前に保存されたベクトルペア $\widehat{s}_i,\widehat{y}_i$ を次の接空間 $T_{p_{k+1}}\mathcal M$ に移動する必要があります。空きメモリがない場合、最も古いペア $\widehat{s}_i,\widehat{y}_i$ を破棄し、残りのベクトルペア $\widehat{s}_i,\widehat{y}_i$ を接空間 $T_{p_{k+1}}\mathcal M$ に移動する必要があります。その後、新しい値 $s_k = \widehat{s}_k = T^{S}_{x_k, α_k η_k}(α_k η_k)$ と $y_k = \widehat{y}_k$ が最初に保存されます。このプロセスは、目的関数に関する新しい情報が常に含まれ、古い、もはや関連性のない情報が破棄されることを保証します。

# 提供されるファンクタ

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` 更新方向を計算する
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` `η` の場所で更新方向を計算する

# フィールド

  * `memory_s`:                保存された（および移動された）探索方向のセット、ステップサイズ $\{\widehat{s}_i\}_{i=k-m}^{k-1}$。
  * `memory_y`:                保存された勾配差のセット $\{\widehat{y}_i\}_{i=k-m}^{k-1}$。
  * `ξ`:                       二重ループ再帰で使用される変数。
  * `ρ`:                       二重ループ再帰で使用される変数。
  * `initial_scale`:           ヘッセ行列の初期スケーリング、（前処理器を使用する場合など）`nothing` を渡すことで無効化
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `message`:                 発生する可能性のある警告を含む文字列
  * `project!`:                接空間に投影することで更新を安定化させる関数

# コンストラクタ

```
QuasiNewtonLimitedMemoryDirectionUpdate(
    M::AbstractManifold,
    x,
    update::AbstractQuasiNewtonUpdateRule,
    memory_size::Int;
    initial_vector=zero_vector(M,x),
    initial_scale::Real=1.0
    project!=copyto!
)
```

# 参照

[`InverseBFGS`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
