```
patricle_swarm(M, f; kwargs...)
patricle_swarm(M, f, swarm; kwargs...)
patricle_swarm(M, mco::AbstractManifoldCostObjective; kwargs..)
patricle_swarm(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
particle_swarm!(M, f, swarm; kwargs...)
particle_swarm!(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

粒子群最適化アルゴリズム (PSO) を実行して

$$
\operatorname*{arg\,min}_{p ∈ \mathcal M} f(p)
$$

を解きます。

PSO は、初期の `swarm` [BorckmansIshtevaAbsil:2010](@cite) の点の集合から始まります。`swarm` が提供されていない場合、`swarm_size` キーワードが使用されてランダムな点が生成されます。計算は `swarm` のインプレースで実行できます。

この目的のために、粒子の群れ $S = \{s_1, \ldots, s_n\}$ が次の方法で多様体 `M` 上を移動します。各粒子 $s_k^{(i)}$ に対して、新しい粒子の速度 $X_k^{(i)}$ は、アルゴリズムの各ステップ $i$ で次のように計算されます。

$$
X_k^{(i)} = ω \mathcal T_{s_k^{(i)←s_k^{(i-1)}} X_k^{(i-1)} + c r_1  \operatorname{retr}^{-1}_{s_k^{(i)}}(p_k^{(i)}) + s r_2 \operatorname{retr}^{-1}_{s_k^{(i)}}(p),
$$

ここで

  * $$
    s_k^{(i)}
    $$

    は現在の粒子の位置です。
  * $$
    ω
    $$

    は慣性を示します。
  * $$
    c
    $$

    と $s$ はそれぞれ認知的および社会的重みです。
  * $$
    r_j
    $$

    , $j=1,2$ は各粒子とステップごとに新たに計算されるランダム因子です。
  * \mathcal T_{⋅←⋅} はベクトル輸送であり、
  * \operatorname{retr}^{-1} は逆引き戻しです。

次に、粒子の位置は次のように更新されます。

$$
s_k^{(i+1)} = \operatorname{retr}_{s_k^{(i)}}(X_k^{(i)}),
$$

次に、各粒子の最良のエントリ $p_k^{(i)}$ は次のように更新されます。

$$
p_k^{(i+1)} = \begin{cases}
s_k^{(i+1)},  & \text{if } F(s_k^{(i+1)})<F(p_{k}^{(i)}),\\
p_{k}^{(i)}, & \text{else,}
\end{cases}
$$

そして、全体の最良の位置は次のように更新されます。

$$
g^{(i+1)} = \begin{cases}
p_k^{(i+1)},  & \text{if } F(p_k^{(i+1)})<F(g_{k}^{(i)}),\\
g_{k}^{(i)}, & \text{else,}
\end{cases}
$$

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `swarm = [rand(M) for _ in 1:swarm_size]`: 初期の点の群れ。

コスト関数 `f` の代わりに [`AbstractManifoldCostObjective`](@ref) `mco` を提供することもできます。

# キーワード引数

  * `cognitive_weight=1.4`: 認知的重み係数
  * `inertia=0.65`: 粒子の慣性
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `social_weight=1.4`: 社会的重み係数
  * `swarm_size=100`: 群れのサイズ、ランダムに生成する場合
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-4)`: 停止基準が満たされていることを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照
  * `velocity`:                  粒子の速度を表す接ベクトルのセット (型 `AbstractVector{T}`)、初期位置ごとにデフォルトでランダムな接ベクトル

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。目的を直接提供する場合でも、これらの装飾は指定できます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。 ```
