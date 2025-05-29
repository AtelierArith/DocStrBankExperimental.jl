```
Y = transform_moments(X::Matrix, m, Σ; preserve_latin=false)
```

Transforms `X` such that it get the specified mean and covariance.

```julia
m, Σ   = [1,2], [2 1; 1 4] # Desired mean and covariance
particles = transform_moments(X, m, Σ)
julia> cov(particles) ≈ Σ
true
```

**Note**, if `X` is a latin hypercube and `Σ` is non-diagonal, then the latin property is destroyed for all dimensions but the first. We provide a method `preserve_latin=true`) which absolutely preserves the latin property in all dimensions, but if you use this, the covariance of the sample will be slightly wrong
