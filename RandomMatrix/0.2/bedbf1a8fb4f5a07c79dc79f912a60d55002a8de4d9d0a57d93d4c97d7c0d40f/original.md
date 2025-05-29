```julia
ComplexNormal(μ,σ)
```

  * `μ` : mean, `μ = 0` by default
  * `σ` : standard deviation, `σ  =1` by default

```julia
# Examples

# Generates 10 iid standard Complex Gaussian r.v.s
rand(ComplexNormal(), 10) 

# Generates complex normal with mean 1+1im, variance 4
rand(ComplexNormal(1+1im,2)) 
```
