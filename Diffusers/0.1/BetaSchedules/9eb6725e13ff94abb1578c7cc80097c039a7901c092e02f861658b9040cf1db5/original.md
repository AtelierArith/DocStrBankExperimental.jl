Scaled linear beta schedule.

## Input

  * `T::Int`: number of timesteps
  * `β₁::Real=1.0f-4`: initial value of β
  * `β₋₁::Real=2.0f-2`: final value of β

## Output

  * `β::Vector{Real}`: βₜ values at each timestep t

## References

  * [[2006.11239] Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)
