```
NewDist(d::UnivariateDistribution, θ::Vector{Real})
```

Create a new distribution object with updated parameters θ. Parameters not be estimated are ignored.

# Example

```julia
d1 = Normal()
NewDist(d1, [0, 1])

d2 = Binomial(10, 0.4)
NewDist(d2, [0.7])
```
