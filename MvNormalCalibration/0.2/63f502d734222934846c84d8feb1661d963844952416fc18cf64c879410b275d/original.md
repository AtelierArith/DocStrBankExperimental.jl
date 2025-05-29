```
sharpness(pred::Normal)
sharpness(pred::AbstractMvNormal)
```

Compute sharpness for (uni- or multivariate) normal distribution, which we define as the (hyper-)volume of the ellipsoid that contains one standard deviation of the distribution.

# Examples

```julia-repl
julia> sharpness(Normal())
2
julia> sharpness(MvNormal(zeros(2), I(2)))  # recall area of circle=πr^2
π
```
