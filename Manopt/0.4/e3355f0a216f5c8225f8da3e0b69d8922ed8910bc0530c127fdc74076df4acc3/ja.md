```
QuasiNewtonLimitedMemoryDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

この [`AbstractQuasiNewtonDirectionUpdate`](@ref) は、近似演算子が $m$ 個の保存された接ベクトルのペア $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ で表される制限付きメモリのリーマン BFGS 更新を表します。探索方向 $η_k$ の計算には、一般化された二重ループ再帰が使用されます（詳細は [HuangGallivanAbsil:2015](@cite) を参照）。これは、$T_{x_k} \mathcal{M}$ 内の接ベクトルの内積と線形結合のみを必要とします。そのため、保存された接ベクトルのペア $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$、目的関数 $f$ の勾配 $\operatorname{grad}f(x_k)$ および正定値自己随伴演算子

$$
\mathcal{B}^{(0)}_k[⋅] = \frac{g_{x_k}(s_{k-1}, y_{k-1})}{g_{x_k}(y_{k-1}, y_{k-1})} \; \mathrm{id}_{T_{x_k} \mathcal{M}}[⋅]
$$

が使用されます。二重ループ再帰は、[`InverseBFGS`](@ref) 更新が $\mathcal{B}^{(0)}_k[⋅]$ に対して接ベクトル $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ を用いて $m$ 回連続して実行され、同時に結果として得られた演算子 $\mathcal{B}^{LRBFGS}_k [⋅]$ が $\operatorname{grad}f(x_k)$ に直接適用されると理解できます。更新時には二つのケースがあります：まだ空きメモリがある場合、$k < m$ のときは、以前に保存されたベクトルペア $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ を次の接空間 $T_{x_{k+1}} \mathcal{M}$ に移動する必要があります。空きメモリがない場合は、最も古いペア $\{ \widetilde{s}_{k−m}, \widetilde{y}_{k−m}\}$ を破棄し、残りのベクトルペア $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m+1}^{k-1}$ を接空間 $T_{x_{k+1}} \mathcal{M}$ に移動します。その後、新しい値 $s_k = \widetilde{s}_k = T^{S}_{x_k, α_k η_k}(α_k η_k)$ および $y_k = \widetilde{y}_k$ が最初に保存されます。このプロセスにより、目的関数に関する新しい情報が常に含まれ、古い、もはや関連性のない情報が破棄されることが保証されます。

# 提供されるファンクタ

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` 更新方向を計算する
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` `η` の場所で更新方向を計算する

# フィールド

  * `memory_s`                保存された（および移動された）探索方向のセット、ステップサイズ $\{ \widetilde{s}_i\}_{i=k-m}^{k-1}$。
  * `memory_y`                保存された勾配の差のセット $\{ \widetilde{y}_i\}_{i=k-m}^{k-1}$。
  * `ξ`                       二重ループ再帰で使用される変数。
  * `ρ`                       二重ループ再帰で使用される変数。
  * `scale`                   ヘッセ行列の初期スケーリング
  * `vector_transport_method` `AbstractVectorTransportMethod`
  * `message`                 発生する可能性のある警告を含む文字列

# コンストラクタ

```
QuasiNewtonLimitedMemoryDirectionUpdate(
    M::AbstractManifold,
    x,
    update::AbstractQuasiNewtonUpdateRule,
    memory_size;
    initial_vector=zero_vector(M,x),
    scale::Real=1.0
    project::Bool=true
)
```

# 参照

[`InverseBFGS`](@ref) [`QuasiNewtonCautiousDirectionUpdate`](@ref) [`AbstractQuasiNewtonDirectionUpdate`](@ref)
