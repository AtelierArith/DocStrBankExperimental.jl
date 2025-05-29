Add noise to clean data using the forward diffusion process.

## Input

  * `scheduler::Scheduler`: scheduler to use
  * `x₀::AbstractArray`: clean data to add noise to
  * `ϵ::AbstractArray`: noise to add to clean data
  * `t::AbstractArray`: timesteps used to weight the noise

## Output

  * `xₜ::AbstractArray`: noisy data at the given timesteps
