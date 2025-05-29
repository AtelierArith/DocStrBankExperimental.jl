```
CosSumGaussian{D,V}( n_cos, n_gaussians, k, α, σ, μ, δ )
```

Data type for parameters of initial distribution

$$
(1+ \cos( \sum^{n_{cos}}_{i=1} k_i x)) 
\cdot 
\sum_{j=1}^{n_{gaussians}} 
\delta_j 
\exp \big( -\frac{1}{2} 
\frac{(v-\mu_j)^2}{\sigma_j^2} \big)
$$

## Parameters

  * `k` : values of the wave numbers (one array for each cosines)
  * `α` : strength of perturbations
  * `σ` : variance of the Gaussian (one velocity vector for each gaussian).
  * `μ` : mean value of the Gaussian (one velocity vector for each gaussian).
  * `δ` : portion of each Gaussian

# Example

$$
f(x,v_1,v_2)=\frac{1}{2\pi\sigma_1\sigma_2} \exp \Big( - \frac{1}{2}
\big( \frac{v_1^2}{\sigma_1^2} + \frac{v_2^2}{\sigma_2^2} \big) 
\Big) ( 1 + \alpha \cos(kx)),
$$

```julia
df = CosSumGaussian{1,2}([[k]],[α], [[σ₁,σ₂]], [[μ₁,μ₂]])
```
