```
Log([λ = 1])
```

Logarithm covariance function with correlation length `λ` and variance `σ² = ∞`.

Used for generating the Gaussian Multiplicative Chaos.

It is defined as $C(r) = \log\left(\frac{\lambda}{r}\right)$.

# Examples

```jldoctest
julia> logcov = Log(1.5)
Log{Float64}(λ=1.5)

julia> logcov(0)
Inf

julia> logcov(1.5)
0.0
```
