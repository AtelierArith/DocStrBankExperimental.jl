```
canonicallink(D::Distribution)
```

Return the canonical link for distribution `D`, which must be in the exponential family.

# Examples

```jldoctest; setup = :(using GLM)
julia> canonicallink(Bernoulli())
LogitLink()
```
