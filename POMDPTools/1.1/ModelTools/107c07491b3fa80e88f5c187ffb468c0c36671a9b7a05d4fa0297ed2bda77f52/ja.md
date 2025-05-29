```
SparseTabularMDP
```

整数の状態とアクションを持つMDPオブジェクトで、遷移はスパース行列のリストで表されます。このデータ構造は、ベクトル化されたアルゴリズム（例：SparseValueIterationSolverを参照）で利用するのに役立ちます。遷移行列と報酬行列にアクセスする推奨の方法は、提供されたアクセサ関数 `transition_matrix` と `reward_vector` を通じてです。

# フィールド

  * `T::Vector{SparseMatrixCSC{Float64, Int64}}` 遷移モデルは、スパース行列のベクトル（各アクションごとに1つ）として表されます。`T[a][s, sp]` は、アクション `a` を取ることで状態 `s` から `sp` への遷移の確率です。
  * `R::Array{Float64, 2}` 報酬は、行が状態、列がアクションの行列として表されます：`R[s, a]` は、状態 `s` でアクション `a` を取ることの報酬です。
  * `initial_probs::SparseVector{Float64, Int64}` 初期状態分布を指定します。
  * `terminal_states::Set{Int64}` 終端状態を格納します。
  * `discount::Float64` 割引率です。

# コンストラクタ

  * `SparseTabularMDP(mdp::MDP)` : デフォルトコンストラクタに行列を提供することも、明示的インターフェースを使用して定義された任意の離散状態MDPから `SparseTabularMDP` を構築することもできます。

遷移行列と報酬行列を構築するには、すべての状態を反復処理する必要があり、時間がかかる場合があります。明示的インターフェースを使用してMDPを定義する方法についての詳細は、https://juliapomdp.github.io/POMDPs.jl/latest/explicit/ を訪れてください。

  * `SparseTabularMDP(smdp::SparseTabularMDP; transition, reward, discount)` : このコンストラクタは、キーワード引数で指定されたフィールドを除いて、元のsmdpのコピーである新しいスパースMDPを返します。
