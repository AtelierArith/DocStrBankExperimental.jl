```
μ ∓ σ
```

Creates 100 `StaticParticles` with mean `μ` and std `σ`. If `μ` is a vector, the constructor `MvNormal` is used, and `σ` is thus treated as std if it's a scalar, and variances if it's a matrix or vector. See also [`±`](@ref), [`⊗`](@ref)
