```
params!{D<:AbstractMvLogNormal}(::Type{D},m::AbstractVector,S::AbstractMatrix,μ::AbstractVector,Σ::AbstractMatrix)
```

Calculate (scale,location) for a given mean and covariance, and store the results in `μ` and `Σ`
