```
apply(cov, pts...)
```

Returns the covariance matrix, i.e., the covariance function `cov` evaluated in the points `x`.

# Examples

```jldoctest
julia> exponential_covariance = CovarianceFunction(1, Exponential(1))
1d exponential covariance function (λ=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=11)
0.0:0.1:1.0

julia> C = apply(exponential_covariance, pts);

julia> heatmap(C);

julia> whittle_covariance = CovarianceFunction(2, Whittle(1))
2d Whittle covariance function (λ=1.0, σ=1.0, p=2.0)

julia> C = apply(whittle_covariance, pts, pts);

julia> heatmap(C);

```

See also: [`CovarianceFunction`](@ref), [`Exponential`](@ref), [`Whittle`](@ref)
