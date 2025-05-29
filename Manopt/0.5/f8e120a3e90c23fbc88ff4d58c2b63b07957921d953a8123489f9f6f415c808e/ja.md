```
QuasiNewtonCautiousDirectionUpdate <: AbstractQuasiNewtonDirectionUpdate
```

これらの [`AbstractQuasiNewtonDirectionUpdate`](@ref) は、いわゆる慎重な更新に基づく任意の準ニュートン更新ルールを表します。探索方向は [`QuasiNewtonMatrixDirectionUpdate`](@ref) または [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) に示されるように計算されますが、更新は次の条件が満たされる場合にのみ実行されます。

$$
\frac{g_{x_{k+1}}(y_k,s_k)}{\lVert s_k \rVert^{2}_{x_{k+1}}} ≥ θ(\lVert \operatorname{grad}f(x_k) \rVert_{x_k}),
$$

ここで、$θ$ は $θ(0) = 0$ を満たし、$0$ で厳密に増加する単調増加関数です。これが満たされない場合、対応する更新はスキップされ、[`QuasiNewtonMatrixDirectionUpdate`](@ref) の場合、行列 $H_k$ または $B_k$ は更新されません。それでも、基底 $\{b_i\}^{n}_{i=1}$ は次の接空間 $T_{x_{k+1}} \mathcal{M}$ に輸送され、[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) の場合、最も古いベクトルペア $\{ \widetilde{s}_{k−m}, \widetilde{y}_{k−m}\}$ は破棄されず、最新のベクトルペア $\{ \widetilde{s}_{k}, \widetilde{y}_{k}\}$ はストレージに追加されず、すべての保存されたベクトルペア $\{ \widetilde{s}_i, \widetilde{y}_i\}_{i=k-m}^{k-1}$ が接空間 $T_{x_{k+1}} \mathcal{M}$ に輸送されます。もし [`InverseBFGS`](@ref) または [`InverseBFGS`](@ref) が更新として選択された場合、結果として得られる方法は [HuangAbsilGallivan:2018](@cite) の方法に従い、対応するステップサイズが選択されることを考慮します。

# 提供されるファンクタ

  * `(mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` 更新方向を計算する
  * `(η, mp::AbstractManoptproblem, st::QuasiNewtonState) -> η` `η` のインプレースで更新方向を計算する

# フィールド

  * `update`: [`AbstractQuasiNewtonDirectionUpdate`](@ref)
  * `θ`:      $θ(0) = 0$ を満たし、$0$ で厳密に増加する単調増加関数。

# コンストラクタ

```
QuasiNewtonCautiousDirectionUpdate(U::QuasiNewtonMatrixDirectionUpdate; θ = identity)
QuasiNewtonCautiousDirectionUpdate(U::QuasiNewtonLimitedMemoryDirectionUpdate; θ = identity)
```

行列ベースまたは制限付きメモリベースの更新ルールのいずれかに対して慎重な更新を生成します。

# 参照

[`QuasiNewtonMatrixDirectionUpdate`](@ref) [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) ```
