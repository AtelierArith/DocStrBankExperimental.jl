```
SingularCovariance{T}
```

Supertype for singular covariance functions. 

Singular means that the variance $\sigma^2 = \infty$.

## Examples

```jldoctest
julia> Log{Float64}<:SingularCovariance{Float64}
true
```
