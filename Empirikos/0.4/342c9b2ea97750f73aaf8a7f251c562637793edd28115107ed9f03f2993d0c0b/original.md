```
pdf(prior::Distribution, Z::EBayesSample)
```

Given a `prior` $G$ and `EBayesSample` $Z$, compute the marginal density of `Z`.

# Examples

```jldoctest
julia> Z = StandardNormalSample(1.0)
Z=     1.0 | σ=1.0
julia> prior = Normal(2.0, sqrt(3))
Normal{Float64}(μ=2.0, σ=1.7320508075688772)
julia> pdf(prior, Z)
0.17603266338214976
julia> pdf(Normal(2.0, 2.0), 1.0)
0.17603266338214976
```
