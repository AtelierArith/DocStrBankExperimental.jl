bootstrap

Bootstrap method for estimating the parameters of a power law distribution. To quantify the uncertainty in our estimate for xmin you can use bootstrap method. More information can be found in this document [Power-law distributions in empirical data](http://arxiv.org/pdf/0706.1062v2.pdf).

# Arguments

  * `data::AbstractArray`: Data to be tested.
  * `d::UnivariateDistribution`: Distribution to be tested (`ContinuousPowerLaw` or `DiscretePowerLaw`).
  * `no_of_sims::Int64`: Number of simulations. Default is `10`.
  * `xmins::AbstractArray`: Array of xmins to be tested, default is `data`.
  * `xmax::Int64`: Maximum value of data to be considered. Default is `1e5`.
  * `seed::Int64`: Seed for random number generator. Default is `0`.

# Returns

  * `statistic::Array{Tuple{UnivariateDistribution, Float64}}`: Array of tuples containing the distribution and the Kolmogorov-Smirnov distance between the data and the distribution.
