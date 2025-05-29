```
patricle_swarm(M, f; kwargs...)
patricle_swarm(M, f, swarm; kwargs...)
patricle_swarm(M, mco::AbstractManifoldCostObjective; kwargs..)
patricle_swarm(M, mco::AbstractManifoldCostObjective, swarm; kwargs..)
```

粒子群最適化アルゴリズム（PSO）を実行し、初期の `swarm` から開始します [BorckmansIshtevaAbsil:2010](@cite)。`swarm` が提供されていない場合、`swarm_size` 個のランダムな点が使用されます。

PSOの目的は、次の式をおおよそ解く `Manifold M` 上の粒子位置 $p$ を見つけることです。

$$
\min_{p ∈\mathcal{M}} F(p).
$$

この目的のために、粒子の群れ $S = \{s_1, \ldots, s_n\}$ が次の方法で多様体 `M` の周りを移動します。各粒子 $s_k^{(i)}$ に対して、アルゴリズムの各ステップ $i$ で新しい粒子速度 $X_k^{(i)}$ が次のように計算されます。

$$
  X_k^{(i)} = ω \, \operatorname{T}_{s_k^{(i)}\gets s_k^{(i-1)}}X_k^{(i-1)} + c r_1  \operatorname{retr}_{s_k^{(i)}}^{-1}(p_k^{(i)}) + s r_2 \operatorname{retr}_{s_k^{(i)}}^{-1}(p),
$$

ここで

  * $$
    s_k^{(i)}
    $$

    は現在の粒子位置、
  * $$
    ω
    $$

    は慣性を示します、
  * $$
    c
    $$

    と $s$ はそれぞれ認知的および社会的重みです、
  * $$
    r_j
    $$

    , $j=1,2$ は各粒子とステップごとに新たに計算されるランダム因子です
  * $$
    T
    $$

    はベクトル輸送を示し、$\operatorname{retr}^{-1}$ は使用される逆引き戻しを示します

次に、粒子の位置は次のように更新されます。

$$
s_k^{(i+1)} = \operatorname{retr}_{s_k^{(i)}}(X_k^{(i)}),
$$

ここで $\operatorname{retr}$ は `Manifold` `M` 上の引き戻しを示します。次に、各粒子の最良のエントリ $p_k^{(i)}$ が次のように更新されます。

$$
p_k^{(i+1)} = \begin{cases}
s_k^{(i+1)},  & \text{if } F(s_k^{(i+1)})<F(p_{k}^{(i)}),\\
p_{k}^{(i)}, & \text{else,}
\end{cases}
$$

そして、全体の最良の位置は

$$
g^{(i+1)} = \begin{cases}
p_k^{(i+1)},  & \text{if } F(p_k^{(i+1)})<F(g_{k}^{(i)}),\\
g_{k}^{(i)}, & \text{else,}
\end{cases}
$$

# 入力

  * `M`:     多様体 $\mathcal M$
  * `f`:     最小化するコスト関数 $F:\mathcal M→ℝ$
  * `swarm`: （`[rand(M) for _ in 1:swarm_size]`）初期の点の群れ。

コスト関数 `f` の代わりに [`AbstractManifoldCostObjective`](@ref) `mco` を提供することもできます。

# オプション

  * `cognitive_weight`:          （`1.4`）認知的重み係数
  * `inertia`:                   （`0.65`）粒子の慣性
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M, eltype(swarm))`）使用する逆引き戻し。
  * `swarm_size`:                （`100`）ランダムに生成する場合の群れのサイズ
  * `retraction_method`:         （`default_retraction_method(M, eltype(swarm))`）使用する引き戻し。
  * `social_weight`:             （`1.4`）社会的重み係数
  * `stopping_criterion`:        （[`StopAfterIteration`](@ref)`(500) |`[`StopWhenChangeLess`](@ref)`(1e-4)`) [`StoppingCriterion`](@ref) から継承されたファンクタで、いつ停止するかを示します。
  * `vector_transport_method`:   （`default_vector_transport_method(M, eltype(swarm))`）使用するベクトル輸送方法。
  * `velocity`:                  粒子の速度を表す接ベクトルのセット（型 `AbstractVector{T}`）、初期位置ごとにデフォルトでランダムな接ベクトル

他のすべてのキーワード引数は、デコレーター用の [`decorate_state!`](@ref) またはそれぞれの目的用の [`decorate_objective!`](@ref) に渡されます。直接 [`ManifoldGradientObjective`](@ref) を提供する場合でも、これらの装飾を指定することができます。

# 出力

得られた（おおよその）最小化者 $g$、詳細は [`get_solver_return`](@ref) を参照してください。 ```
