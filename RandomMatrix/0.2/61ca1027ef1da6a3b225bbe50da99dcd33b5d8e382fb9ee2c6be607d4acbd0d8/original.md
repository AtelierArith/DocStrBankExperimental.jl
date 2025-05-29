```julia
Gaussian(beta,μ,σ)
```

  * `beta` : 1 (default) for Real Gaussian, 2 for Complex Gaussian
  * `μ` : mean, `μ = 0` by default
  * `σ` : standard deviation, `σ  =1` by default

```julia
# Generates 10 iid standard normal r.v.s
rand(Gaussian(), 10) 

# Generates a complex normal with mean 1+1im, variance 4
rand(Gaussian(2,1+1im,2))
```
