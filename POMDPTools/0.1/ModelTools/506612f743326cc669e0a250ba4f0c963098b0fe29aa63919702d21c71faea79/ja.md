```
SparseTabularPOMDP
```

状態と行動が整数であり、遷移および観測分布が疎行列のリストで表されるPOMDPオブジェクトです。このデータ構造は、ベクトル化されたアルゴリズムで性能を向上させるために利用するのに役立ちます（例：SparseValueIterationSolverを参照）。遷移、報酬、および観測行列にアクセスする推奨の方法は、提供されたアクセサ関数 `transition_matrix`、`reward_vector`、`observation_matrix` を通じて行うことです。

# フィールド

  * `T::Vector{SparseMatrixCSC{Float64, Int64}}` 遷移モデルは疎行列のベクトル（各行動ごとに1つ）として表されます。`T[a][s, sp]` は、行動 `a` を取ることで状態 `s` から `sp` への遷移の確率です。
  * `R::Array{Float64, 2}` 報酬は行が状態、列が行動の行列として表されます：`R[s, a]` は状態 `s` で行動 `a` を取ることの報酬です。
  * `O::Vector{SparseMatrixCSC{Float64, Int64}}` 観測モデルは疎行列のベクトル（各行動ごとに1つ）として表されます。`O[a][sp, o]` は、行動 `a` を取った後に状態 `sp` から観測 `o` を得る確率です。
  * `initial_probs::SparseVector{Float64, Int64}` 初期状態分布を指定します。
  * `terminal_states::Set{Int64}` 終端状態を格納します。
  * `discount::Float64` 割引率です。

# コンストラクタ

  * `SparseTabularPOMDP(pomdp::POMDP)` : デフォルトコンストラクタに行列を提供することも、明示的インターフェースを使用して定義された任意の離散状態MDPから `SparseTabularPOMDP` を構築することもできます。

遷移および報酬行列を構築するには、すべての状態を反復処理する必要があり、時間がかかる場合があります。明示的インターフェースを使用してMDPを定義する方法についての詳細は、https://juliapomdp.github.io/POMDPs.jl/latest/explicit/ を訪れてください。

  * `SparseTabularPOMDP(spomdp::SparseTabularMDP; transition, reward, observation, discount)` : このコンストラクタは、キーワード引数で指定されたフィールドを除いて、元のsmdpのコピーである新しい疎POMDPを返します。
