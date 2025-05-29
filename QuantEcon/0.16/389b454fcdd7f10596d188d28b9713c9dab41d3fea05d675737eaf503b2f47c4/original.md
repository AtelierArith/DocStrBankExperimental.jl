computes log-likelihood of entire observations

##### Arguments

  * `kn::Kalman`: `Kalman` specifying the model. Initial value must be the prior               for t=1 period observation, i.e. $x_{1|0}$.
  * `y::AbstractMatrix`: `n x T` matrix of observed data.                      `n` is the number of observed variables in one period.                      Each column is a vector of observations at each period.

##### Returns

  * `logL::Real`: log-likelihood of all observations
