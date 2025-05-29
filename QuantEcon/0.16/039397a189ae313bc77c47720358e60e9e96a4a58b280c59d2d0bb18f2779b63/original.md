##### Arguments

  * `kn::Kalman`: `Kalman` specifying the model. Initial value must be the prior               for t=1 period observation, i.e. $x_{1|0}$.
  * `y::AbstractMatrix`: `n x T` matrix of observed data.                      `n` is the number of observed variables in one period.                      Each column is a vector of observations at each period.

##### Returns

  * `x_smoothed::AbstractMatrix`: `k x T` matrix of smoothed mean of states.                               `k` is the number of states.
  * `logL::Real`: log-likelihood of all observations
  * `sigma_smoothed::AbstractArray` `k x k x T` array of smoothed covariance matrix of states.
