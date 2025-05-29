```
Covariance{T}
```

Supertype for 'true' (non-singular) covariance functions.

Non-singular means that the variance $\sigma^2 < \infty$.

## Examples

```jldoctest
julia> Exponential{Float32}<:Covariance{Float32}
true

julia> Linear{Int16}<:Covariance{Int16}
true
```
