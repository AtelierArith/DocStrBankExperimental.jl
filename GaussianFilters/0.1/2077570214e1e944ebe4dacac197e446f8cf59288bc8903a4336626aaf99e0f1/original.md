unscented*transform(b::GaussianBelief, λ::Int=2, α::Number=1,     β::Number=0; decomp*method::String = "cholesky")

Convert a single GaussianBelief (mean and covariance) to set of 2n+1 sigma points, with n being the dimensionality of the state space. Return an array of the points, and arrays for weights used in mean and covariance calculations. Uses formulation from ProbRob for α/β parameters on a separate covariance weighting, although this is not necessary.
