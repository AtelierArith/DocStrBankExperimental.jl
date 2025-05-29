Remove noise from model output using the backward diffusion process.

## Input

  * `scheduler::Scheduler`: scheduler to use
  * `xₜ::AbstractArray`: sample to be denoised
  * `ϵᵧ::AbstractArray`: predicted noise to remove
  * `t::AbstractArray`: timestep t of `xₜ`

## Output

  * `xₜ₋₁::AbstractArray`: denoised sample at t=t-1
  * `x̂₀::AbstractArray`: denoised sample at t=0
