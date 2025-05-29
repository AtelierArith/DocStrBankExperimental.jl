```
SwitchingGaussianRegression(; 
    K::Int,
    input_dim::Int,
    output_dim::Int,
    include_intercept::Bool = true,
    β::Matrix{<:Real} = if include_intercept
        zeros(input_dim + 1, output_dim)
    else
        zeros(input_dim, output_dim)
    end,
    Σ::Matrix{<:Real} = Matrix{Float64}(I, output_dim, output_dim),
    λ::Float64 = 0.0,
    A::Matrix{<:Real} = initialize_transition_matrix(K),
    πₖ::Vector{Float64} = initialize_state_distribution(K)
)
```

スイッチングガウス回帰モデルを作成します

# 引数

  * `K::Int`: 隠れ状態の数。
  * `input_dim::Int`: 入力特徴の次元数。
  * `output_dim::Int`: 出力予測の次元数。
  * `include_intercept::Bool`: 回帰モデルに切片を含めるかどうか（デフォルトは `true`）。
  * `β::Matrix{<:Real}`: 回帰係数（`input_dim` と `output_dim` に基づいてゼロにデフォルト設定）。
  * `Σ::Matrix{<:Real}`: ガウス排出の共分散行列（単位行列にデフォルト設定）。
  * `λ::Float64`: 回帰の正則化パラメータ（デフォルトは `0.0`）。
  * `A::Matrix{<:Real}`: 隠れマルコフモデルの遷移行列（ランダム初期化にデフォルト設定）。
  * `πₖ::Vector{Float64}`: 隠れマルコフモデルの初期状態分布（ランダム初期化にデフォルト設定）。

# 戻り値

  * `::HiddenMarkovModel`: スイッチングガウス回帰モデル
