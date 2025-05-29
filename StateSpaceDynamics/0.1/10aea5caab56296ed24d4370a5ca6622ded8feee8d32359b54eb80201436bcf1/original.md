# ProbabilisticPCA(;W::Matrix{<:AbstractFloat}, σ²:: <: AbstractFloat, μ::Matrix{<:AbstractFloat}, k::Int, D::Int)

# Constructor for ProbabilisticPCA model.

# # Args:

# - `W::Matrix{<:AbstractFloat}`: Weight matrix that maps from latent space to data space.

# - `σ²:: <: AbstractFloat`: Noise variance

# - `μ::Matrix{<:AbstractFloat}`: Mean of the data

# - `k::Int`: Number of latent dimensions

# - `D::Int`: Number of features

# # Example:

# ```julia

# # PPCA with unknown parameters

# ppca = ProbabilisticPCA(k=1, D=2)

# # PPCA with known parameters

# ppca = ProbabilisticPCA(W=rand(2, 1), σ²=0.1, μ=rand(2), k=1, D=2)

# ```

# 
