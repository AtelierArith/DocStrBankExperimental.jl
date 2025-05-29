bootstrap_p

Performs a bootstrapping hypothesis test to determine whether a power law distribution is plausible. Inspired by R [poweRlaw](http://arxiv.org/pdf/1407.3492v1.pdf) documentation.

# Arguments

  * `data::AbstractArray`: Data to be tested.
  * `d::UnivariateDistribution`: Distribution to be tested (`ContinuousPowerLaw` or `DiscretePowerLaw`).
  * `no_of_sims::Int64`: Number of simulations. Default is `10`.
  * `xmins::AbstractArray`: Array of xmins to be tested, default is `data`.
  * `xmax::Int64`: Maximum value of data to be considered. Default is `1e5`.
  * `seed::Int64`: Seed for random number generator. Default is `0`.

# Returns

  * `statistic::Array{Tuple{UnivariateDistribution, Float64}}`: Array of tuples containing the distribution and the Kolmogorov-Smirnov distance between the data and the distribution.
  * `P::Float64`: p-value of the hypothesis test.
