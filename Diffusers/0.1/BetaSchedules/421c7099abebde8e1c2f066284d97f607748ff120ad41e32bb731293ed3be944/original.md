Cosine beta schedule.

## Input

  * `T::Int`: number of timesteps
  * `βₘₐₓ::Real=0.999f0`: maximum value of β
  * `ϵ::Real=1.0f-3`: small value used to avoid division by zero

## Output

  * `β::Vector{Real}`: βₜ values at each timestep t

## References

  * [[2102.09672] Improved Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2102.09672)
  * [github:openai/improved-diffusion](https://github.com/openai/improved-diffusion/blob/783b6740edb79fdb7d063250db2c51cc9545dcd1/improved_diffusion/gaussian_diffusion.py#L36)
