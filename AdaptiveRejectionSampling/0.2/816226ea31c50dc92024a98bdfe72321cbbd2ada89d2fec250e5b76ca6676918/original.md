RejectionSampler(f::Function, support::Tuple{Float64, Float64}, init::Tuple{Float64, Float64})     RejectionSampler(f::Function, support::Tuple{Float64, Float64}[ ,δ::Float64]) An adaptive rejection sampler to obtain iid samples from a logconcave function supported in  `support = (support[1], support[2])`. f can either be the either probability density of the  function to be sampled, or its logarithm. For the latter, use the keyword argument `log=true`.  The functions can be unnormalized in the sense that the probability density can be specified up to a constant.  The adaptive rejection samplings algorithm requires two initial points `init = init[1], init[2]` such that (d/dx)logp(init[1]) > 0 and (d/dx)logp(init[2]) < 0. These points can be provided directly (typically, any point left and right of the mode will do). It is also possibe to specify and search range and delta for a greedy search of the initial points.  The `support` must be of the form `(-Inf, Inf), (-Inf, a), (b, Inf), (a,b)`, and it represent the interval in which f has positive value, and zero elsewhere.

The alternative constructor uses a search_range, a value δ for the distance between points in the search, and min/max slope values in absolute terms.

## Keyword arguments

  * `max_segments::Int = 10` : max size of envelop, the rejection-rate is usually slow with a small number of segments
  * `max_failed_factor::Float64 = 0.001`: level at which throw an error if one single sample has a rejection rate   exceeding this value
  * `logdensity::Bool = false`: indicator fo whether `f` is the log of the probability density, up to a normalization constant.
  * `search_range::Tuple{Float64,Float64} = (-10.0, 10.0)`: range in which to search for initial points
  * `min_slope::Float64 = 1e-6`: minimum slope in absolute value of logf at the initial/found points
  * `max_slope::Float64 = Inf: maximum slope in absolute value of logf at the initial/found points
