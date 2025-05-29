```
SumCosGaussian( dims, n_cos, n_gaussians, k, α, σ, μ, δ )
```

Data type for parameters of initial distribution

$$
(1+ \sum_{i=1}^{n_{cos}} \alpha_i \cos(  k_i \mathbf{x}))
\cdot
\sum_{j=1}^{n_{gaussians}} 
\delta_j \exp 
\big( -\frac{1}{2} 
\frac{(\mathbf{v}-\mu_j)^2}{\sigma_j^2} \big)
$$

## Parameters

  * `k` : values of the wave numbers (Array of vectors for multiple cosines)
  * `α` : strength of perturbations
  * `σ` : variance of the Gaussian ( Array of vectors for multiple Gaussians)
  * `μ` : mean value of the Gaussian ( Array multiple Gaussians)
  * `normal` : Normalization constant of each Gaussian
  * `n_gaussians` : Number of Gaussians
  * `n_cos` : Number of cosines
  * `δ` : portion of each Gaussian

# Example

$$
f(x,v_1,v_2) = \frac{1}{2\pi\sigma_1\sigma_2} 
\exp \Big( - \frac{1}{2} \big( \frac{v_1^2}{\sigma_1^2}
 + \frac{v_2^2}{\sigma_2^2} \big) \Big) 
( 1 + \alpha_1 \cos(k_1 x) + \alpha_2 \cos(k_2 x) ),
$$

```julia
df = SumCosGaussian{1,2}([[k₁],[k₂]], [α₁, α₂], [[σ₁,σ₂]], [[0.0,0.0]])

```
