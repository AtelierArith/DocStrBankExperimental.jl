```
GaussianHMM(; K::Int, output_dim::Int, A::Matrix{<:Real}=initialize_transition_matrix(K), πₖ::Vector{Float64}=initialize_state_distribution(K))
```

ガウス排出を持つ隠れマルコフモデルを作成します

# 引数

  * `K::Int`: 隠れ状態の数
  * `output_dim::Int`: 観測の次元
  * `A::Matrix{<:Real}=initialize_transition_matrix(K)`: HMMの遷移行列（デフォルトはランダム初期化）
  * `πₖ::Vector{Float64}=initialize_state_distribution(K)`: HMMの初期状態分布（デフォルトはランダム初期化）

# 戻り値

  * `::HiddenMarkovModel`: ガウス排出を持つ隠れマルコフモデルオブジェクト

```
