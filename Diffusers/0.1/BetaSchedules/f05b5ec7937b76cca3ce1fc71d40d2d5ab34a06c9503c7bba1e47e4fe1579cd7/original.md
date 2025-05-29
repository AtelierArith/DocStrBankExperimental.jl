Rescale betas to have zero terminal Signal to Noise Ratio (SNR).

## Input

  * `β::AbstractArray`: βₜ values at each timestep t

## Output

  * `β::Vector{Real}`: rescaled βₜ values at each timestep t

## References

  * [[2305.08891] Rescaling Diffusion Models](https://arxiv.org/abs/2305.08891) (Alg. 1)
