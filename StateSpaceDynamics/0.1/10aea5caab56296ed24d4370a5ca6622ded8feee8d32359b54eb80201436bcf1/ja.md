# ProbabilisticPCA(;W::Matrix{<:AbstractFloat}, σ²:: <: AbstractFloat, μ::Matrix{<:AbstractFloat}, k::Int, D::Int)

# ProbabilisticPCAモデルのコンストラクタ。

# # 引数:

# - `W::Matrix{<:AbstractFloat}`: 潜在空間からデータ空間へのマッピングを行う重み行列。

# - `σ²:: <: AbstractFloat`: ノイズの分散

# - `μ::Matrix{<:AbstractFloat}`: データの平均

# - `k::Int`: 潜在次元の数

# - `D::Int`: 特徴の数

# # 例:

# ```julia

# # パラメータが不明なPPCA

# ppca = ProbabilisticPCA(k=1, D=2)

# # パラメータが既知のPPCA

# ppca = ProbabilisticPCA(W=rand(2, 1), σ²=0.1, μ=rand(2), k=1, D=2)

# ```
