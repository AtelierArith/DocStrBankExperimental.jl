```
SwitchingBernoulliRegression(; K::Int, input_dim::Int, include_intercept::Bool=true, β::Vector{<:Real}=if include_intercept zeros(input_dim + 1) else zeros(input_dim) end, λ::Float64=0.0, A::Matrix{<:Real}=initialize_transition_matrix(K), πₖ::Vector{Float64}=initialize_state_distribution(K))
```

スイッチングベルヌーイ回帰モデルの作成

# 引数

  * `K::Int`: 隠れ状態の数。
  * `input_dim::Int`: 入力データの次元。
  * `include_intercept::Bool=true`: 回帰モデルに切片を含めるかどうか（デフォルトはtrue）。
  * `β::Vector{<:Real}`: 回帰係数（デフォルトはゼロ）。
  * `λ::Float64=0.0`: 回帰の正則化パラメータ（デフォルトはゼロ）。
  * `A::Matrix{<:Real}=initialize_transition_matrix(K)`: HMMの遷移行列（デフォルトはランダム初期化）。
  * `πₖ::Vector{Float64}=initialize_state_distribution(K)`: HMMの初期状態分布（デフォルトはランダム初期化）。

# 戻り値

  * `::HiddenMarkovModel`: スイッチングベルヌーイ回帰モデル
