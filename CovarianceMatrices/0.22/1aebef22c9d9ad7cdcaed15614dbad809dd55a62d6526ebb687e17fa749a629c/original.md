Asymptotic Variance Estimators

aVar(k::AVarEstimator, m::AbstractMatrix{T}; demean::Bool=true, dims::Int=1, means::Union{Nothing, AbstractArray}=nothing, prewhite::Bool=false, scale=true)

## Arguments

```
- k::AVarEstimator 
- `demean=false`: whether the data should be demeaned.    
- `prewhite=false`: should the data be prewithened. Relevant for `HAC` estimator.
```
