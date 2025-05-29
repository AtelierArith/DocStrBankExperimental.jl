generate_msm(μ::Vector{Float64}, σ::Vector{Float64}, P::Matrix{Float64}, T::Int64; <keyword arguments>)

Generate artificial data from Markov switching model from provided parameters. Returns a tuple of `(y, s_t, X)` where `y` is the generated data, `s_t` is the state sequence and `X` is the design matrix.

Note, in order to have non-switching parameter provide it k-times.

# Arguments

  * `μ::Vector{AbstractFloat}`: intercepts for each state.
  * `σ::Vector{AbstractFloat}`: standard deviations for each state.
  * `P::Matrix{AbstractFloat}`: transition matrix.
  * `T::Int64`: number of observations to generate.
  * `β::Vector{AbstractFloat}`: switching coefficients. (first k elements in vector are coefficeints of the first state equation).
  * `β_ns::Vector{AbstractFloat}`: non-switching coefficients.
  * `δ::Vector{AbstractFloat}`: tvtp coefficients.
  * `tvtp_intercept::Bool`: whether to include an intercept in the tvtp model.
