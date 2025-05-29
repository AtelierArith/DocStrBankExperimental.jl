Compute a simulated sample path assuming Gaussian shocks.

##### Arguments

  * `arma::ARMA`: Instance of `ARMA` type
  * `;ts_length::Integer(90)`: Length of simulation
  * `;impulse_length::Integer(30)`: Horizon for calculating impulse response (see also docstring for `impulse_response`)

##### Returns

  * `X::Vector{Float64}`: Simulation of the ARMA model `arma`
