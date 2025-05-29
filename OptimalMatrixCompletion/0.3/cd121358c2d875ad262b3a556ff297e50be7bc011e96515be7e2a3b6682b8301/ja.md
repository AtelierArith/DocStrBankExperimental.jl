```
branchandbound_frob_matrixcomp(
    k::Int,
    A::Array{Float64, 2},
    indices::BitMatrix,
    γ::Float64,
    λ::Float64,
    noise::Bool,
    ;
    <keyword arguments>
)
```

観測されたインデックス `indices` を持つ行列 `A` をランク-`k` 行列 `X` で補完します。

ノイズがある場合（`noise == true`）、次の問題を解きます（正則化パラメータ `γ` を使用）：

$$
\min_{\mathbf{X}}
\frac{1}{2} \sum_{(i,j) \in \mathcal{I}} (X_{i,j} - A_{i,j})^2 
+ \frac{1}{2 \gamma} \|\mathbf{X}\|_F^2
\quad 
\text{s.t. } \text{Rank}(\mathbf{X}) \leq k
$$

ノイズがない場合（`noise == false`）、次の問題を解きます：

$$
\min_{\mathbf{X}}
\|\mathbf{X}\|_F^2
\quad 
\text{s.t. } X_{i,j} = A_{i,j} \ \forall (i,j) \in \mathcal{I}, 
\ \text{Rank}(\mathbf{X}) \leq k
$$

# 引数

  * `branching_type::Union{String, Nothing} = nothing`: `use_disjunctive_cuts = false` の場合、どの座標で分岐するかを決定します："lexicographic" または "bounds" または "gradient" のいずれか；
  * `branch_point::Union{String, Nothing} = nothing`: `use_disjunctive_cuts = false` の場合、どの値で分岐するかを決定します："midpoint" または "current_point" のいずれか；
  * `node_selection::String = "breadthfirst"`: 使用するノード選択戦略："breadthfirst" または "bestfirst" または "depthfirst" または "bestfirst_depthfirst" のいずれか；
  * `bestfirst_depthfirst_cutoff::Int = 10000`: `node_selection = "bestfirst_depthfirst"` の場合、アルゴリズムが `"bestfirst"` から `"depthfirst"` に切り替わる前のキュー内のノード数；
  * `gap::Float64 = 1e-4`: 分岐限定アルゴリズムの相対最適性ギャップ；
  * `use_disjunctive_cuts::Bool = true`: 固有ベクトルの不連続性を使用するかどうか、`true` を推奨；
  * `disjunctive_cuts_type::Union{String, Nothing} = nothing`: 区分線形上近似の部分数；"linear"（2部分）または "linear2"（3部分）または "linear3"（4部分）のいずれか；
  * `disjunctive_cuts_breakpoints::Union{String, Nothing} = nothing`: 分離オラクルを構築するために使用する固有ベクトルの数；"smallest*1*eigvec"（最も負の固有ベクトル）または "smallest*2*eigvec"（最も負の固有ベクトルの組み合わせ）；
  * `presolve::Bool = false`: ノイズのない設定（`noise = false`）で、事前解決を行うかどうか、`true` を推奨；
  * `add_basis_pursuit_valid_inequalities::Bool = false`: ノイズのない設定（`noise = false`）で、行列式の小行列から有効な不等式を課すかどうか；
  * `add_Shor_valid_inequalities::Bool = false`: 各ノードでSDP緩和を強化するためにShor SDP不等式を追加するかどうか；
  * `Shor_valid_inequalities_noisy_rank1_num_entries_present::Vector{Int} = [1, 2, 3, 4]`: `add_Shor_valid_inequalities` が `true` の場合、Shor SDP不等式でモデル化する2-by-2行列式の小行列のセット、埋められたエントリの数に基づく（`[1, 2, 3, 4]` の部分集合であるべき）；
  * `add_Shor_valid_inequalities_fraction::Float64 = 1.0`: `add_Shor_valid_inequalities` が `true` の場合、Shor SDP不等式でモデル化する2-by-2行列式の小行列の割合；
  * `add_Shor_valid_inequalities_iterative::Bool = false`: `add_Shor_valid_inequalities` が `true` の場合、親ノードから子ノードに不等式を逐次追加するかどうか；
  * `max_update_Shor_indices_probability::Float64 = 1.0`: `add_Shor_valid_inequalities_iterative` が `true` の場合、ノードで不等式を追加する最大確率；
  * `min_update_Shor_indices_probability::Float64 = 0.1`: `add_Shor_valid_inequalities_iterative` が `true` の場合、ノードで不等式を追加する最小確率；
  * `update_Shor_indices_probability_decay_rate::Float64 = 1.1`: `add_Shor_valid_inequalities_iterative` が `true` の場合、ツリーの深さの関数としてノードで不等式を追加する確率の指数減衰の基数；
  * `update_Shor_indices_n_minors::Int = 100`: `add_Shor_valid_inequalities_iterative` が `true` の場合、追加が行われるときにノードで追加するShor SDP不等式の数；
  * `root_only::Bool = false`: `true` の場合、ルートノードでのみ緩和を解決します；
  * `altmin_flag::Bool = true`: 分岐限定ツリーのノードで交互最小化を行うかどうか、`true` を推奨；
  * `max_altmin_probability::Float64 = 1.0`: `altmin_flag` が `true` の場合、ノードで交互最小化を行う最大確率；
  * `min_altmin_probability::Float64 = 0.005`: `altmin_flag` が `true` の場合、ノードで交互最小化を行う最小確率；
  * `altmin_probability_decay_rate::Float64 = 1.1`: `altmin_flag` が `true` の場合、ツリーの深さの関数としてノードで交互最小化を行う確率の指数減衰の基数；
  * `use_max_steps::Bool = false`: 探索された分岐限定ノードの数に基づいてアルゴリズムを終了するかどうか；
  * `max_steps::Int = 1000000`: `use_max_steps` が `true` の場合、探索された分岐限定ノードの上限；
  * `time_limit::Int = 3600`: 秒単位の時間制限；
  * `update_step::Int = 1000`: 印刷された更新ごとに探索された分岐限定ノードの数；
