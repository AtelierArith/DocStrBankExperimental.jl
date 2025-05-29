generatemixture(N, K; [α, dim, radius, σ, rng])

Generates a multivariate Normal mixture, with kernel weights generated from a Dirichlet prior. The kernels are centred at the vertices of a `dim`-dimensional simplex with edge length `radius`.

# Required Arguments

  * `N::Integer`: number of observations to generate.
  * `K::Integer`: number of mixture kernels.

# Optional Arguments

  * `α::Float64 = K`: parameter for the Dirichlet prior.
  * `dim::Integer = K`: dimension of the observations.
  * `radius::Float64 = 1`: radius of the simplex whose vertices are the kernel means.
  * `σ::Float64 = 0.1`: variance of each kernel.
  * `rng`: a random number generator to use, or an integer to seed the default random number generator with. If not provided, the default RNG provided by the Random.jl package will be used with default seeding.

# Returns

Named tuple containing the following fields-

  * `points::Vector{Vector{Float64}}`: a vector of `N` observations.
  * `distancematrix::Matrix{Float64}`: an `N`×`N` matrix of pairwise Euclidean distances between the observations.
  * `clusts::ClustLabelVector`: vector of `N` cluster assignments.
  * `probs::Float64`: vector of `K` cluster weights generated from the Dirichlet prior, used to generate the observations.
  * `oracle_coclustering::Matrix{Float64}`: `N`×`N` matrix of co-clustering probabilities, calculated assuming full knowledge of the cluster centres and cluster weights.
