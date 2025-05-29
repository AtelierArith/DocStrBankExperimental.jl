```
quasi_Newton(M, f, grad_f, p; kwargs...)
quasi_Newton!(M, f, grad_f, p; kwargs...)
```

準ニュートン反復を実行して

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} f(p)
$$

を解きます。開始点は `p` です。反復は `p$=p^{(0)}$` のインプレースで行うことができます。$k$ 番目の反復は次のようになります。

1. 探索方向 $η^{(k)} = -\mathcal B_k [\operatorname{grad}f (p^{(k)})]$ を計算するか、$\mathcal H_k [η^{(k)}] = -\operatorname{grad}f (p^{(k)})]$ を解きます。
2. 曲線 $γ(α) = R_{p^{(k)}}(α η^{(k)})$ に沿った適切なステップサイズ $α_k$ を決定します。通常は [`WolfePowellLinesearch`](@ref) を使用します。
3. $$
    p^{(k+1)} = R_{p^{(k)}}(α_k η^{(k)})
    $$

    を計算します。
4. $$
    s_k = \mathcal T_{p^{(k)}, α_k η^{(k)}}(α_k η^{(k)})
    $$

    と $y_k = \operatorname{grad}f(p^{(k+1)}) - \mathcal T_{p^{(k)}, α_k η^{(k)}}(\operatorname{grad}f(p^{(k)}))$ を定義します。ここで、$\mathcal T$ はベクトル輸送を示します。
5. 新しい近似ヘッセ行列 $H_{k+1}$ またはその逆行列 $B_{k+1}$ を計算します。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: 関数 `(M, p) -> X` または関数 `(M, X, p) -> X` で `X` をインプレースで計算する $f$ の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `basis=`[`DefaultOrthonormalBasis`](@extref ManifoldsBase.DefaultOrthonormalBasis)`()`: ヘッセ行列 (逆行列) を完全な (行列) 形式で保存する場合に、接空間内で使用する基底。
  * `cautious_update=false`: [`QuasiNewtonCautiousDirectionUpdate`](@ref) を使用するかどうか。これは `direction_upate` をラップします。
  * `cautious_function=(x) -> x * 1e-4`: $x=0$ でゼロになり、$0$ で厳密に増加する慎重な更新のための単調増加関数。
  * `direction_update=`[`InverseBFGS`](@ref)`()`: 使用する [`AbstractQuasiNewtonUpdateRule`](@ref)。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、結果を割り当てるか ([`AllocatingEvaluation`](@ref))、または入力引数を修正してその中で結果を返すか ([`InplaceEvaluation`](@ref)) を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。例えば `grad_f(M,p)` は割り当てますが、`grad_f!(M, X, p)` は `X` のインプレースで結果を計算します。
  * `initial_operator= initial_scale*Matrix{Float64}(I, n, n)`: ヘッセ行列 (逆行列) の近似が完全な行列として保存される場合に使用する初期行列。これは `n=manifold_dimension(M)` の場合にのみ割り当てられます。この行列は完全な行列の場合にのみ割り当てられます。`initial_scale` も参照してください。
  * `initial_scale=1.0`: 限定メモリアプローチの計算において $\frac{s⟨s_k,y_k⟩_{p_k}}{\lVert y_k\rVert_{p_k}}$ に使用する初期 `s` のスケール。`initial_operator` も参照してください。
  * `memory_size=20`: 限定メモリ、保存する $s_k, y_k$ の数。負の値に設定すると、完全メモリ (行列) 表現を使用します。
  * `nondescent_direction_behavior=:reinitialize_direction_update`: 非降下方向がどのように処理されるかを指定します。これは次のようになります。

      * `:step_towards_negative_gradient`: 方向が負の勾配に置き換えられ、メッセージが保存されます。
      * `:ignore`: 検証が行われず、計算された方向が受け入れられます。メッセージは保存されません。
      * `:reinitialize_direction_update`: 方向更新ルールに保存されたオペレータの状態を破棄します。
      * その他の値は検証を行い、方向を保持しますが、メッセージを保存します。

    保存されたメッセージは [`DebugMessages`](@ref) を使用して表示できます。
  * `preconditioner=nothing` 前処理器を指定します。これは次のいずれかです。

      * デフォルトの `nothing` は前処理を有効にしません。
      * 形式 `(M, p, X) -> Y` または変更可能な `(M, Y, p, X) -> Y` の関数で、`evaluation` に依存します。
      * [`PreconditionedDirection`](@ref)。前処理器に関する詳細は、ドキュメントを参照してください。

    前処理器は勾配に適用されます。すなわち、線形システムを解く前の右辺です。
  * `project!=copyto!`: 数値的安定性のため、各反復後に接空間に投影することが可能です。この関数は `Y` のインプレースで動作する必要があります。すなわち、`(M, Y, p, X) -> Y` であり、`X` と `Y` は同じメモリである可能性があります。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$。再収束に関するセクションを参照してください [@extref ManifoldsBase :doc:`retractions`]。
  * `stepsize=`[`WolfePowellLinesearch`](@ref)`(retraction_method, vector_transport_method)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(max(1000, memory_size))`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: 停止基準が満たされていることを示すファンクタ。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$。ベクトル輸送に関するセクションを参照してください [@extref ManifoldsBase :doc:`vector_transports`]。

その他のキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。
