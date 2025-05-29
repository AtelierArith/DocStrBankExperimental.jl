```
quasi_Newton(M, f, grad_f, p)
```

マンifold `M` 上の点 `p` から始めて、関数 `f` に対して準ニュートン反復を実行します。

$$
k
$$

番目の反復は次のようになります。

1. 探索方向 $η_k = -\mathcal{B}_k [\operatorname{grad}f (p_k)]$ を計算するか、$\mathcal{H}_k [η_k] = -\operatorname{grad}f (p_k)]$ を解きます。
2. 曲線 $\gamma(α) = R_{p_k}(α η_k)$ に沿った適切なステップサイズ $α_k$ を決定します。通常は [`WolfePowellLinesearch`](@ref) を使用します。
3. `p_{k+1} = R_{p_k}(α_k η_k)` を計算します。
4. $$
    s_k = T_{p_k, α_k η_k}(α_k η_k)
    $$

    および $y_k = \operatorname{grad}f(p_{k+1}) - T_{p_k, α_k η_k}(\operatorname{grad}f(p_k))$ を定義します。
5. 新しい近似ヘッセ行列 $H_{k+1}$ またはその逆行列 $B_k$ を計算します。

# 入力

  * `M`      マンifold $\mathcal{M}$。
  * `f`      最小化するコスト関数 $F : \mathcal{M} →ℝ$。
  * `grad_f` 関数 $F$ の勾配 $\operatorname{grad}F : \mathcal{M} →T_x\mathcal M$。
  * `p`      初期値 $p ∈ \mathcal{M}$。

# オプション

  * `basis`:                   (`DefaultOrthonormalBasis()`) ヘッセ行列（逆行列）を表すための接空間内の基底。

  * `cautious_update`:         (`false`) [`QuasiNewtonCautiousDirectionUpdate`](@ref) を使用するかどうか。
  * `cautious_function`:       (`(x) -> x*10^(-4)`) 0でゼロになり、0で厳密に増加する単調増加関数（慎重な更新用）。
  * `direction_update`:        ([`InverseBFGS`](@ref)`()`) 使用する更新ルール。
  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するか（デフォルト）`gradF(M, p)` の形式、または [`InplaceEvaluation`](@ref) の形式 `gradF!(M, X, p)` であるかを指定します。
  * `initial_operator`:        (`Matrix{Float64}(I, n, n)`) 近似に使用する初期行列、ここで `n=manifold_dimension(M)`、`scale_initial_operator` も参照。
  * `memory_size`:             (`20`) 限定メモリ、保存する $s_k, y_k$ の数。負の値を設定するとフルメモリ表現を使用します。
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) 使用する再収束法。
  * `scale_initial_operator`:  (`true`) 計算において初期オペレーターを $\frac{⟨s_k,y_k⟩_{p_k}}{\lVert y_k\rVert_{p_k}}$ でスケールします。
  * `stabilize`:               (`true`) 計算された（ニュートン）方向を接空間に投影して数値誤差を減らすことにより、数値的にメソッドを安定化します。
  * `stepsize`:                ([`WolfePowellLinesearch`](@ref)`(retraction_method, vector_transport_method)`) [`Stepsize`](@ref) を指定します。
  * `stopping_criterion`:      ([`StopAfterIteration`](@ref)`(max(1000, memory_size)) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`) [`StoppingCriterion`](@ref) を指定します。
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) 使用するベクトル輸送。
  * `nondescent_direction_behavior`: (`:reinitialize_direction_update`) 非降下方向がどのように処理されるかを指定します。これには次のものが含まれます。

      * `:step_towards_negative_gradient`: 方向が負の勾配に置き換えられ、メッセージが保存されます。
      * `:ignore`: 検証が行われず、計算された方向が受け入れられます。メッセージは保存されません。
      * `:reinitialize_direction_update`: 方向更新ルールに保存されたオペレーターの状態を破棄します。
      * その他の値は検証を行い、方向を保持しますが、メッセージを保存します。

    保存されたメッセージは [`DebugMessages`](@ref) を使用して表示できます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。 ```
