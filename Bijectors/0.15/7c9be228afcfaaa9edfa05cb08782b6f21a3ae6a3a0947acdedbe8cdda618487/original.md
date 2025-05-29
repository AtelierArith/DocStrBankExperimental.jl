```
logpdf_with_trans(d::Distribution, x, transform::Bool)
```

If `transform` is `false`, `logpdf_with_trans` calculates the log probability density function (logpdf) of distribution `d` at `x`.

If `transform` is `true`, `x` is transformed using the constrained-to-unconstrained bijector for distribution `d`, and then the logpdf of the resulting value is calculated with respect to the unconstrained (transformed) distribution. Equivalently, if `x` is distributed according to `d` and `y = link(d, x)` is distributed according to `td = transformed(d)`, then `logpdf_with_trans(d, x, true) = logpdf(td, y)`. This is accomplished by subtracting the log Jacobian of the transformation.

# Example

```jldoctest
julia> using Bijectors

julia> logpdf_with_trans(LogNormal(), ℯ, false)
-2.4189385332046727

julia> logpdf(LogNormal(), ℯ)  # Same as above
-2.4189385332046727

julia> logpdf_with_trans(LogNormal(), ℯ, true)
-1.4189385332046727

julia> # If x ~ LogNormal(), then log(x) ~ Normal()
       logpdf(Normal(), 1.0)   
-1.4189385332046727

julia> # The difference between the two is due to the Jacobian
       logabsdetjac(bijector(LogNormal()), ℯ)
-1
```
