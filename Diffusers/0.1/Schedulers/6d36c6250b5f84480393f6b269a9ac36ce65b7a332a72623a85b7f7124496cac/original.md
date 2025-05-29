Compute the velocity of the diffusion process.

## Input

  * `scheduler::Scheduler`: scheduler to use
  * `x₀::AbstractArray`: clean data to add noise to
  * `ϵ::AbstractArray`: noise to add to clean data
  * `t::AbstractArray`: timesteps used to weight the noise

## Output

  * `vₜ::AbstractArray`: velocity at the given timesteps

## References

  * [[2202.00512] Progressive Distillation for Fast Sampling of Diffusion Models](https://arxiv.org/abs/2202.00512) (Ann. D)
